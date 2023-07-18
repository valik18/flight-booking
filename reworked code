#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_HISTORY_SIZE 100

typedef struct {
    char origin[20];
    char destination[20];
    char departure[10];
    char arrival[10];
    int price;
} Flight;

typedef struct {
    char name[50];
    char dob[15];
    char gender[10];
    char nationality[20];
    char passport[20];
    char email[50];
    char phone[20];
} Passenger;

typedef struct {
    Flight flight;
    Passenger passenger;
} Reservation;

Reservation history[MAX_HISTORY_SIZE];
int historyCount = 0;

void enterPassportDetails(Passenger *passenger) {
    printf("Введіть паспортні дані пасажира:\n");
    printf("Повне ім'я: ");
    scanf(" %[^\n]s", passenger->name);

    printf("Дата народження: ");
    scanf(" %[^\n]s", passenger->dob);

    printf("Стать: ");
    scanf(" %[^\n]s", passenger->gender);

    printf("Громадянство: ");
    scanf(" %[^\n]s", passenger->nationality);

    printf("Номер паспорта: ");
    scanf(" %[^\n]s", passenger->passport);
}

void enterContactDetails(Passenger *passenger) {
    printf("Введіть контактні дані пасажира:\n");
    printf("Електронна пошта: ");
    scanf(" %[^\n]s", passenger->email);

    printf("Телефон: ");
    scanf(" %[^\n]s", passenger->phone);
}

void addToHistory(Flight flight, Passenger passenger) {
    if (historyCount < MAX_HISTORY_SIZE) {
        Reservation reservation = { .flight = flight, .passenger = passenger };
        history[historyCount++] = reservation;
    } else {
        printf("Історія резервування квитків заповнена. Неможливо додати новий рейс.\n");
    }
}

void printHistory() {
    printf("Історія резервування квитків:\n");

    for (int i = 0; i < historyCount; i++) {
        Flight flight = history[i].flight;
        Passenger passenger = history[i].passenger;

        printf("Рейс %d: %s (виліт о %s, прибуття о %s) Ціна: %d\n",
            i + 1, flight.destination, flight.departure, flight.arrival, flight.price);
        printf("   Повне ім'я: %s\n", passenger.name);
        printf("   Дата народження: %s\n", passenger.dob);
        printf("   Стать: %s\n", passenger.gender);
        printf("   Громадянство: %s\n", passenger.nationality);
        printf("   Номер паспорта: %s\n", passenger.passport);
        printf("   Електронна пошта: %s\n", passenger.email);
        printf("   Телефон: %s\n", passenger.phone);
    }
}

void bookTicket() {
    Flight flights[] = {
        { "Жуляни (IEV)", "Одеса (ODS)", "09:30", "11:00", 1800 },
        { "Жуляни (IEV)", "Скнилів (LWO)", "10:00", "11:30", 1300 },
        { "Жуляни (IEV)", "Харків (HRK)", "08:30", "09:30", 1400 },
        { "Жуляни (IEV)", "Сімферополь (SIP)", "11:30", "13:00", 1600 },
        { "Жуляни (IEV)", "Дніпро (DNK)", "09:00", "10:00", 1900 },
        { "Жуляни (IEV)", "Запоріжжя (OZH)", "10:30", "12:00", 2500 },
        { "Жуляни (IEV)", "Миколаїв (NLV)", "11:00", "12:30", 2199 },
        { "Жуляни (IEV)", "Івано-Франківськ (IFO)", "09:30", "11:00", 2200 },
        { "Жуляни (IEV)", "Херсон (KHE)", "10:00", "11:30", 4500 },
        { "Жуляни (IEV)", "Вінниця (VIN)", "11:30", "12:30", 3700 },
        { "Жуляни (IEV)", "Чернівці (CWC)", "10:30", "12:00", 3300 },
        { "Жуляни (IEV)", "Ужгород (UDJ)", "09:00", "10:30", 3000 },
        { "Жуляни (IEV)", "Кривий Ріг (KWG)", "10:00", "11:30", 1900 }
    };

    int flightNum, seatNum;
    Flight flight;
    Passenger passenger;

    printf("Виберіть номер рейсу:\n");
    for (int i = 0; i < sizeof(flights) / sizeof(flights[0]); i++) {
        printf("%d. %s - %s\n", i + 1, flights[i].origin, flights[i].destination);
    }

    printf("Ваш вибір: ");
    scanf("%d", &flightNum);

    if (flightNum < 1 || flightNum > sizeof(flights) / sizeof(flights[0])) {
        printf("Невірний номер рейсу.\n");
        return;
    }

    flight = flights[flightNum - 1];

    printf("Виберіть номер місця (1-50): ");
    scanf("%d", &seatNum);

    enterPassportDetails(&passenger);
    enterContactDetails(&passenger);

    addToHistory(flight, passenger);

    printf("\nБронювання успішно завершено!\n");
    printf("Ім'я: %s\n", passenger.name);
    printf("Електронна пошта: %s\n", passenger.email);
    printf("Телефон: %s\n", passenger.phone);
    printf("Рейс: %d\n", flightNum);
    printf("Місце: %d\n", seatNum);
    printf("Ціна: %d\n", flight.price);
}

int main() {
    printf("Система бронювання авіаквитків\n");
    bookTicket();
    printHistory();
    return 0;
}
