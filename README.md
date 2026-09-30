# TASK-11-WORD-AND-CHARACTER-COUNTER
import re


def analyze_text(text):
    """Return statistics for the given paragraph."""
    if not text or not text.strip():
        return None  # handle empty input

    characters_with_spaces = len(text)
    characters_no_spaces = len(text.replace(" ", ""))
    spaces = text.count(" ")
    words = len(text.split())

    # Split on . ! ? and ignore empty pieces (handles "..." and trailing spaces)
    sentences = [s for s in re.split(r"[.!?]+", text) if s.strip()]

    return {
        "Characters (with spaces)": characters_with_spaces,
        "Characters (without spaces)": characters_no_spaces,
        "Words": words,
        "Sentences": len(sentences),
        "Spaces": spaces,
    }


def main():
    sample = (
        "Python is a powerful language. It is easy to learn! "
        "Do you want to build something cool? Let's get started."
    )

    print("Sample paragraph:")
    print(sample, "\n")

    choice = input("Press Enter to use the sample, or type 'own' to enter your paragraph: ")
    text = input("Enter your paragraph: ") if choice.strip().lower() == "own" else sample

    stats = analyze_text(text)
    if stats is None:
        print("Error: no text was entered.")
        return

    print("\n--- Text Statistics ---")
    for label, value in stats.items():
        print(f"{label}: {value}")


if __name__ == "__main__":
    main()
