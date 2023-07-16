#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Структура для збереження даних рейсу
typedef struct {
    char origin[20];
    char destination[20];
    char departure[10];
    char arrival[10];
    int price;
} Flight;

// Структура для збереження даних пасажира
typedef struct {
    char name[50];
    char dob[15];
    char gender[10];
    char nationality[20];
    char passport[20];
    char email[50];
    char phone[20];
} Passenger;

// Масив для збереження історії резервування квитків
#define MAX_HISTORY_SIZE 100
typedef struct {
    Flight flight;
    Passenger passenger;
} Reservation;

Reservation history[MAX_HISTORY_SIZE];
int historyCount = 0;

// Функція для вибору рейсу
int chooseFlight() {
    int flight;
    
    printf("Виберіть номер рейсу:\n");
    printf("1. Жуляни (IEV) - Одеса (ODS)\n");
    printf("2. Жуляни (IEV) - Скнилів (LWO)\n");
    printf("3. Жуляни (IEV) - Харків (HRK)\n");
    printf("4. Жуляни (IEV) - Сімферополь (SIP)\n");
    printf("5. Жуляни (IEV) - Дніпро (DNK)\n");
    printf("6. Жуляни (IEV) - Запоріжжя (OZH)\n");
    printf("7. Жуляни (IEV) - Миколаїв (NLV)\n");
    printf("8. Жуляни (IEV) - Івано-Франківськ (IFO)\n");
    printf("9. Жуляни (IEV) - Херсон (KHE)\n");
    printf("10. Жуляни (IEV) - Вінниця (VIN)\n");
    printf("11. Жуляни (IEV) - Чернівці (CWC)\n");
    printf("12. Жуляни (IEV) - Ужгород (UDJ)\n");
    printf("13. Жуляни (IEV) - Кривий Ріг (KWG)\n");
    
    printf("Ваш вибір: ");
    scanf("%d", &flight);
    
    return flight;
}

// Функція для вибору місця
int chooseSeat() {
    int seat;
    
    printf("Виберіть номер місця (1-50): ");
    scanf("%d", &seat);
    
    return seat;
}

// Функція для введення паспортних даних пасажира
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

// Функція для введення контактних даних пасажира
void enterContactDetails(Passenger *passenger) {
    printf("Введіть контактні дані пасажира:\n");
    printf("Електронна пошта: ");
    scanf(" %[^\n]s", passenger->email);
    
    printf("Телефон: ");
    scanf(" %[^\n]s", passenger->phone);
}

// Функція для додавання резервування до історії
void addToHistory(Flight flight, Passenger passenger) {
    if (historyCount < MAX_HISTORY_SIZE) {
        Reservation reservation;
        reservation.flight = flight;
        reservation.passenger = passenger;
        history[historyCount] = reservation;
        historyCount++;
    } else {
        printf("Історія резервування квитків заповнена. Неможливо додати новий рейс.\n");
    }
}

// Функція для виведення історії резервування квитків
void printHistory() {
    printf("Історія резервування квитків:\n");
    
    for (int i = 0; i < historyCount; i++) {
        printf("Рейс %d: %s (виліт о %s, прибуття о %s) Ціна: %d\n", i + 1, history[i].flight.destination, history[i].flight.departure, history[i].flight.arrival, history[i].flight.price);
        printf("   Повне ім'я: %s\n", history[i].passenger.name);
        printf("   Дата народження: %s\n", history[i].passenger.dob);
        printf("   Стать: %s\n", history[i].passenger.gender);
        printf("   Громадянство: %s\n", history[i].passenger.nationality);
        printf("   Номер паспорта: %s\n", history[i].passenger.passport);
        printf("   Електронна пошта: %s\n", history[i].passenger.email);
        printf("   Телефон: %s\n", history[i].passenger.phone);
    }
}

// Основна функція для бронювання квитка
void bookTicket() {
    int flightNum, seatNum;
    Flight flight;
    Passenger passenger;
    
    // Вибір рейсу
    flightNum = chooseFlight();
    
    // Вибір місця
    seatNum = chooseSeat();
    
    // Введення паспортних даних
    enterPassportDetails(&passenger);
    
    // Введення контактних даних
    enterContactDetails(&passenger);
    
    // Перевірка вибраного рейсу і налаштування відповідних даних
    switch (flightNum) {
        case 1:
            strcpy(flight.origin, "Жуляни (IEV)");
            strcpy(flight.destination, "Одеса (ODS)");
            strcpy(flight.departure, "09:30");
            strcpy(flight.arrival, "11:00");
            flight.price = 1800;
            break;
        case 2:
            strcpy(flight.origin, "Жуляни (IEV)");
            strcpy(flight.destination, "Скнилів (LWO)");
            strcpy(flight.departure, "10:00");
            strcpy(flight.arrival, "11:30");
            flight.price = 1300;
            break;
        case 3:
            strcpy(flight.origin, "Жуляни (IEV)");
            strcpy(flight.destination, "Харків (HRK)");
            strcpy(flight.departure, "08:30");
            strcpy(flight.arrival, "09:30");
            flight.price = 1400;
            break;
        case 4:
            strcpy(flight.origin, "Жуляни (IEV)");
            strcpy(flight.destination, "Сімферополь (SIP)");
            strcpy(flight.departure, "11:30");
            strcpy(flight.arrival, "13:00");
            flight.price = 1600;
            break;
        case 5:
            strcpy(flight.origin, "Жуляни (IEV)");
            strcpy(flight.destination, "Дніпро (DNK)");
            strcpy(flight.departure, "09:00");
            strcpy(flight.arrival, "10:00");
            flight.price = 1900;
            break;
        case 6:
            strcpy(flight.origin, "Жуляни (IEV)");
            strcpy(flight.destination, "Запоріжжя (OZH)");
            strcpy(flight.departure, "10:30");
            strcpy(flight.arrival, "12:00");
            flight.price = 2500;
            break;
        case 7:
            strcpy(flight.origin, "Жуляни (IEV)");
            strcpy(flight.destination, "Миколаїв (NLV)");
            strcpy(flight.departure, "11:00");
            strcpy(flight.arrival, "12:30");
            flight.price = 2199;
            break;
        case 8:
            strcpy(flight.origin, "Жуляни (IEV)");
            strcpy(flight.destination, "Івано-Франківськ (IFO)");
            strcpy(flight.departure, "09:30");
            strcpy(flight.arrival, "11:00");
            flight.price = 2200;
            break;
        case 9:
            strcpy(flight.origin, "Жуляни (IEV)");
            strcpy(flight.destination, "Херсон (KHE)");
            strcpy(flight.departure, "10:00");
            strcpy(flight.arrival, "11:30");
            flight.price = 4500;
            break;
        case 10:
            strcpy(flight.origin, "Жуляни (IEV)");
            strcpy(flight.destination, "Вінниця (VIN)");
            strcpy(flight.departure, "11:30");
            strcpy(flight.arrival, "12:30");
            flight.price = 3700;
            break;
        case 11:
            strcpy(flight.origin, "Жуляни (IEV)");
            strcpy(flight.destination, "Чернівці (CWC)");
            strcpy(flight.departure, "10:30");
            strcpy(flight.arrival, "12:00");
            flight.price = 3300;
            break;
        case 12:
            strcpy(flight.origin, "Жуляни (IEV)");
            strcpy(flight.destination, "Ужгород (UDJ)");
            strcpy(flight.departure, "09:00");
            strcpy(flight.arrival, "10:30");
            flight.price = 3000;
            break;
        case 13:
            strcpy(flight.origin, "Жуляни (IEV)");
            strcpy(flight.destination, "Кривий Ріг (KWG)");
            strcpy(flight.departure, "10:00");
            strcpy(flight.arrival, "11:30");
            flight.price = 1900;
            break;
        default:
            printf("Невірний номер рейсу.\n");
            return;
    }
    
    // Додавання резервування до історії
    addToHistory(flight, passenger);
    
    // Виведення підтвердження
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
    
    // Бронювання авіаквитка
    bookTicket();
    
    // Виведення історії резервування квитків
    printHistory();
    
    return 0;
}
