import random

choices = {
    "rock": "🪨",
    "paper": "📄",
    "scissors": "✂️"
}

def get_computer_choice():
    return random.choice(list(choices.keys()))

def decide_winner(user, computer):
    if user == computer:
        return "draw"
    elif (user == "rock" and computer == "scissors") or \
         (user == "paper" and computer == "rock") or \
         (user == "scissors" and computer == "paper"):
        return "user"
    else:
        return "computer"

print("🎮 Welcome to Rock Paper Scissors Game")

rounds = int(input("Enter number of rounds you want to play: "))

user_score = 0
computer_score = 0

for round_no in range(1, rounds + 1):
    print(f"\n🔹 Round {round_no}")

    user_choice = input("Choose rock, paper, or scissors: ").lower()

    if user_choice not in choices:
        print("❌ Invalid choice! Round skipped.")
        continue

    computer_choice = get_computer_choice()

    print(f"You chose: {choices[user_choice]} ({user_choice})")
    print(f"Computer chose: {choices[computer_choice]} ({computer_choice})")

    result = decide_winner(user_choice, computer_choice)

    if result == "draw":
        print("🤝 It's a draw!")
    elif result == "user":
        print("🎉 You win this round!")
        user_score += 1
    else:
        print("💻 Computer wins this round!")
        computer_score += 1

    print(f"Score → You: {user_score} | Computer: {computer_score}")

print("\n🏁 Game Over!")
print(f"Final Score → You: {user_score} | Computer: {computer_score}")

if user_score > computer_score:
    print("🏆 Congratulations! You won the game!")
elif user_score < computer_score:
    print("😢 Computer won the game!")
else:
    print("🤝 The game ended in a draw!")
