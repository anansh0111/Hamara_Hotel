import tkinter as tk
from tkinter import messagebox

class HotelManagementSystem:
    def __init__(self, root):
        self.root = root
        self.root.title("Hotel Management System")
        self.root.geometry("500x400")
        self.root.config(bg="#f4f4f4")

        self.rooms = {}
        self.check_in_details = {}

        # Setting up the main menu with enhanced UI
        self.setup_main_menu()

    def setup_main_menu(self):
        title_frame = tk.Frame(self.root, bg="#222831", pady=10)
        title_frame.pack(fill="x")

        tk.Label(title_frame, text="Hamara Hotel", font=("Arial", 20, "bold"), fg="white", bg="#222831").pack()

        button_frame = tk.Frame(self.root, bg="#31363F", pady=20)
        button_frame.pack(fill="x")

        tk.Button(button_frame, text="Check In", command=self.check_in_window, bg="#222831", fg="white",
                  font=("Arial", 14), width=20).pack(pady=10)
        tk.Button(button_frame, text="Check Out", command=self.check_out_window, bg="#222831", fg="white",
                  font=("Arial", 14), width=20).pack(pady=10)
        tk.Button(button_frame, text="List Rooms", command=self.list_rooms, bg="#222831", fg="white",
                  font=("Arial", 14), width=20).pack(pady=10)
        tk.Button(button_frame, text="Generate Receipt", command=self.generate_receipt_window, bg="#222831", fg="white",
                  font=("Arial", 14), width=20).pack(pady=10)
        tk.Button(button_frame, text="Exit", command=self.root.quit, bg="#222831", fg="white", font=("Arial", 14), width=20).pack(pady=10)

    def clear_window(self, window):
        for widget in window.winfo_children():
            widget.destroy()

    def check_in_window(self):
        window = tk.Toplevel(self.root)
        window.title("Check In")
        window.geometry("350x200")
        window.config(bg="#31363F")

        tk.Label(window, text="Guest Name:", bg="#f4f4f4", font=("Arial", 12)).grid(row=0, column=0, padx=10, pady=10)
        guest_name = tk.Entry(window, font=("Arial", 12))
        guest_name.grid(row=0, column=1, padx=10, pady=10)

        tk.Label(window, text="Room Number:", bg="#f4f4f4", font=("Arial", 12)).grid(row=1, column=0, padx=10, pady=10)
        room_number = tk.Entry(window, font=("Arial", 12))
        room_number.grid(row=1, column=1, padx=10, pady=10)

        def check_in_action():
            name = guest_name.get()
            room = room_number.get()
            if room in self.rooms:
                messagebox.showerror("Error", f"Room {room} is already occupied.")
            else:
                self.rooms[room] = name
                self.check_in_details[name] = room
                messagebox.showinfo("Success", f"{name} checked into room {room}.")
                window.destroy()

        tk.Button(window, text="Check In", command=check_in_action, bg="#76ABAE", fg="white", font=("Arial", 12)).grid(
            row=2, columnspan=2, pady=10)

    def check_out_window(self):
        window = tk.Toplevel(self.root)
        window.title("Check Out")
        window.geometry("350x200")
        window.config(bg="#31363F")

        tk.Label(window, text="Guest Name:", bg="#f4f4f4", font=("Arial", 12)).grid(row=0, column=0, padx=10, pady=10)
        guest_name = tk.Entry(window, font=("Arial", 12))
        guest_name.grid(row=0, column=1, padx=10, pady=10)

        def check_out_action():
            name = guest_name.get()
            if name in self.check_in_details:
                room = self.check_in_details[name]
                del self.rooms[room]
                del self.check_in_details[name]
                messagebox.showinfo("Success", f"{name} checked out from room {room}.")
                window.destroy()
            else:
                messagebox.showerror("Error", f"No guest found under the name {name}.")

        tk.Button(window, text="Check Out", command=check_out_action, bg="#76ABAE", fg="white", font=("Arial", 12)).grid(
            row=1, columnspan=2, pady=10)

    def list_rooms(self):
        if not self.rooms:
            messagebox.showinfo("Room Status", "All rooms are currently available.")
            return
        room_list = "\n".join([f"Room {room}: {guest}" for room, guest in self.rooms.items()])
        messagebox.showinfo("Room Status", room_list)

    def generate_receipt_window(self):
        window = tk.Toplevel(self.root)
        window.title("Generate Receipt")
        window.geometry("350x200")
        window.config(bg="#31363F")

        tk.Label(window, text="Guest Name:", bg="#f4f4f4", font=("Arial", 12)).grid(row=0, column=0, padx=10, pady=10)
        guest_name = tk.Entry(window, font=("Arial", 12))
        guest_name.grid(row=0, column=1, padx=10, pady=10)

        def generate_receipt_action():
            name = guest_name.get()
            if name in self.check_in_details:
                room = self.check_in_details[name]
                receipt = f"\n--- Receipt ---\nGuest Name: {name}\nRoom Number: {room}\nThank you for staying with us!\n-----------------\n"
                messagebox.showinfo("Receipt", receipt)
                window.destroy()
            else:
                messagebox.showerror("Error", f"No check-in details found for {name}.")

        tk.Button(window, text="Generate", command=generate_receipt_action, bg="#76ABAE", fg="white", font=("Arial", 12)).grid(
            row=1, columnspan=2, pady=10)


# Running the application
if __name__ == "__main__":
    root = tk.Tk()
    app = HotelManagementSystem(root)
    root.mainloop()
