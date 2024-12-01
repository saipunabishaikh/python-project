# python-project
def calculate_duration(age, unit):
    """
    Calculates the duration of time a person has lived based on their age in the specified time unit.
    :param age: Age of the person in years (int).
    :param unit: Time unit as a string ('Months', 'Weeks', 'Days', 'Hours', 'Minutes', 'Seconds').
    :return: The duration lived in the selected time unit.
    """
    # Conversion factors
    conversions = {
        'months': 12,
        'weeks': 52,
        'days': 365,
        'hours': 365 * 24,
        'minutes': 365 * 24 * 60,
        'seconds': 365 * 24 * 60 * 60
    }

    # Normalize user input for unit
    unit = unit.lower()
    if unit.startswith('m'):  # matches 'months' or 'minutes'
        unit = 'months' if unit == 'm' or unit.startswith('mo') else 'minutes'
    elif unit.startswith('w'):
        unit = 'weeks'
    elif unit.startswith('d'):
        unit = 'days'
    elif unit.startswith('h'):
        unit = 'hours'
    elif unit.startswith('s'):
        unit = 'seconds'

    # Calculate duration
    if unit in conversions:
        duration = age * conversions[unit]
        return f"You lived for {duration} {unit.capitalize()}."
    else:
        return "Invalid time unit. Please choose from Months, Weeks, Days, Hours, Minutes, Seconds."


def main():
    print("Welcome to the Age Duration Calculator!")
    try:
        # Get user input for age
        age = int(input("What's your age? "))
        if age < 0:
            print("Age cannot be negative. Please enter a valid age.")
            return

        # Get user input for time unit
        unit = input("Please choose time unit: Months, Weeks, Days, Hours, Minutes, Seconds.\n"
                     "Note: You can write the first letter or the full name of the time unit: ")

        # Calculate and display duration
        result = calculate_duration(age, unit)
        print(result)

    except ValueError:
        print("Invalid input. Please enter a numeric value for age.")


if _name_ == "_main_":
    main()
