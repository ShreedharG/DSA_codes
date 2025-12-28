##### Phase 1 - Design User Abstract Class and Extend User to Rider + Driver

```cpp
#include <string>
#include <algorithm>
#include <stdexcept>
#include <cctype>
using namespace std;

enum class Gender {
    MALE,
    FEMALE,
    OTHER
};

class User {
protected:
    string userID;
    string name;
    Gender gender;
    string mobileNumber;
    string aadharNumber;
    double rating;

    void validateNumber(const string& mobile){
        if(mobile.size() != 10 || !all_of(mobile.begin(), mobile.end(), ::isdigit))
            throw invalid_argument("Invalid mobile number");
    }

    void validateAadhar(const string& aadhar){
        if(aadhar.size() != 12 || !all_of(aadhar.begin(), aadhar.end(), ::isdigit))
            throw invalid_argument("Invalid Aadhar number");
    }

public:
    User(const string& id, const string& name, Gender gender, const string& mobile, const string& aadhar, double initialRating)
        : userID(id), name(name), gender(gender), rating(initialRating) {
        validateNumber(mobile);
        validateAadhar(aadhar);
        this->mobileNumber = mobile;
        this->aadharNumber = aadhar;
    }

    virtual ~User() = default;

    string getID() const { return userID; }
    string getName() const { return name; }
    string getMobileNumber() const { return mobileNumber; }
    double getRating() const { return rating; }
    
    void updateRating ( double newRating ) {
        this->rating = newRating;
    }

    virtual string getRole() const = 0;
};


class Rider : public User {
public:
    Rider(const string& id, const string& name, Gender gender, const string& mobile, const string& aadhar, double initialRating)
        : User(id, name, gender, mobile, aadhar, initialRating) {}

    string getRole () const override {
        return "RIDER";
    }
};


class Vehicle ;

class Driver : public User {
private:
    Vehicle* vehicle;
    bool availability;
public:
    Driver(const string& id, const string& name, Gender gender, const string& mobile, const string& aadhar, double initialRating):
        User(id, name, gender, mobile, aadhar, initialRating) , vehicle(nullptr), availability(true) {}

    bool getAvailability() const {  return availability; }
    Vehicle* getVehicle() const { return vehicle; }
    
    void assignVehicle(Vehicle* v) {
        this->vehicle = v;
    }
    
    void updateAvailability ( bool newAvailability ) {
        availability = newAvailability;
    }

    string getRole() const override {
        return "DRIVER";
    }
};
```
