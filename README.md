# Automatic-Timetable
C++ program to create an automatic class timetable

#include <iostream>
#include <string>

using namespace std;

class Course {
public:
    string name;
    string room;
    int day; // 0 - Monday, 1 - Tuesday, ..., 4 - Friday
    int start_time; // 0 - 12:00 pm, 1 - 1:00 pm, 2 - 2:00 pm, 3 - 3:00 pm
    int duration; // in hours
    bool is_practical;
};

int main() {
    const int NUM_COURSES = 9;
    const int NUM_PRACTICALS = 6;
    Course courses[NUM_COURSES] = {
        {"Com 311", "American Embassy Lab", 0, 1, 2, false},
        {"Com 312", "SGS Building", 0, 2, 2, false},
        {"Com 315", "SGS Building", 1, 1, 2, false},
        {"GNS 301", "SGS Building", 1, 2, 2, false},
        {"Com 313", "SGS Building", 2, 1, 2, false},
        {"Com 316", "SGS Building", 2, 2, 2, false},
        {"Sta 314", "SGS Building", 3, 1, 2, true},
        {"Com 314", "SGS Building", 3, 2, 2, true},
        {"Sta 311", "SGS Building", 4, 2, 2, true}
    };
    Course practicals[NUM_PRACTICALS] = {
        {"Com 311", "American Emb", 0, 0, 2, true},
        {"Com 312", "SGS Hall", 1, 0, 2, true},
        {"Com 313", "Oracle Lab", 2, 0, 2, true},
        {"Com 314", "Hardware Lab", 3, 0, 2, true},
        {"Com 315", "Oracle Lab", 4, 0, 2, true},
        {"Com 316", "Physics Chem Lab", 4, 1, 2, true}
    };
    string days[5] = {"Monday", "Tuesday", "Wednesday", "Thursday", "Friday"};
    string times[4] = {"12:00 pm", "2:00 pm", "4:00 pm"};

    // Get user input
    int day, time;
    cout<< "HND One Evening CS Dept. Automatic Time Table";
    cout<< " ------------------------------------------- \n";
    cout << "Enter day (0 - Monday, 1 - Tuesday, 2 - Wednesday, 3 - Thursday, 4 - Friday): ";
    cin >> day;
    cout<< " ------------------------------------------- \n";
    cout << "Enter the time (0 - 12:00 pm, 1 - 2:00 pm, 2 - 4:00 pm): ";
    cin >> time;
    cout<< " ------------------------------------------- \n";

    // Search for matching course/practical
    bool found = false;
    for (int i = 0; i < NUM_COURSES; i++) {
        if (!courses[i].is_practical && courses[i].day == day && courses[i].start_time == time) {
            cout << "You have " << courses[i].name << " in " << courses[i].room << " at " << times[courses[i].start_time] << " on " << days[courses[i].day] << endl;
            found = true;
            break;
        }
    }
    if (!found) {
        for (int i = 0; i < NUM_PRACTICALS; i++) {
            if (practicals[i].day == day && practicals[i].start_time == time) {
            cout << "You have " << practicals[i].name << " practical in " << practicals[i].room << " at " << times[practicals[i].start_time] << " on " << days[practicals[i].day] << endl;
            found = true;
            break;
     }
   }
  }
if (!found) {
cout << "No courses or practicals found at that time." << endl;
}
return 0;
}
