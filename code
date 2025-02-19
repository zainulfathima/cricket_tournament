class CricketTournament:
    def _init_(self):
        # Store matches as a list of dictionaries
        self.matches = []

    def view_matches(self):
        """View all matches"""
        if not self.matches:
            print("No matches scheduled.")
            return

        print("\nScheduled Matches:")
        for match in self.matches:
            print(f"ID: {match['id']}, Teams: {match['team1']} vs {match['team2']}, Date: {match['date']}, Time: {match['time']}, Location: {match['location']}")

    def add_match(self, team1, team2, date, time, location):
        """Add a new match"""
        # Check for time collision
        for match in self.matches:
            if match['date'] == date and match['time'] == time and match['location'] == location:
                print("A match is already scheduled at this time and location. Please choose a different time or location.")
                return

        match_id = len(self.matches) + 1
        self.matches.append({
            'id': match_id,
            'team1': team1,
            'team2': team2,
            'date': date,
            'time': time,
            'location': location
        })
        print(f"Match added successfully! Match ID: {match_id}")

    def update_match(self, match_id, team1=None, team2=None, date=None, time=None, location=None):
        """Update an existing match"""
        for match in self.matches:
            if match['id'] == match_id:
                # Check for time collision if date, time, or location is updated
                if date or time or location:
                    for other_match in self.matches:
                        if other_match['id'] != match_id and other_match['date'] == (date or match['date']) and other_match['time'] == (time or match['time']) and other_match['location'] == (location or match['location']):
                            print("A match is already scheduled at this time and location. Update failed.")
                            return

                if team1:
                    match['team1'] = team1
                if team2:
                    match['team2'] = team2
                if date:
                    match['date'] = date
                if time:
                    match['time'] = time
                if location:
                    match['location'] = location

                print(f"Match ID {match_id} updated successfully!")
                return

        print("Match ID not found.")

    def cancel_match(self, match_id):
        """Cancel an existing match"""
        for match in self.matches:
            if match['id'] == match_id:
                self.matches.remove(match)
                print(f"Match ID {match_id} canceled successfully!")
                return

        print("Match ID not found.")

# Example usage
def main():
    tournament = CricketTournament()

    while True:
        print("\nCricket Tournament Management")
        print("1. View all matches")
        print("2. Add a match")
        print("3. Update a match")
        print("4. Cancel a match")
        print("5. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            tournament.view_matches()
        elif choice == '2':
            team1 = input("Enter Team 1 name: ")
            team2 = input("Enter Team 2 name: ")
            date = input("Enter match date (YYYY-MM-DD): ")
            time = input("Enter match time (HH:MM): ")
            location = input("Enter match location: ")
            tournament.add_match(team1, team2, date, time, location)
        elif choice == '3':
            match_id = int(input("Enter Match ID to update: "))
            team1 = input("Enter new Team 1 name (leave blank to keep unchanged): ") or None
            team2 = input("Enter new Team 2 name (leave blank to keep unchanged): ") or None
            date = input("Enter new match date (leave blank to keep unchanged): ") or None
            time = input("Enter new match time (leave blank to keep unchanged): ") or None
            location = input("Enter new match location (leave blank to keep unchanged): ") or None
            tournament.update_match(match_id, team1, team2, date, time, location)
        elif choice == '4':
            match_id = int(input("Enter Match ID to cancel: "))
            tournament.cancel_match(match_id)
        elif choice == '5':
            print("Exiting...")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__== "__main__":
    main()
