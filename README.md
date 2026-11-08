# CPP_module_03

CPP Module 03 — 42 Bangkok
Inheritance. Aaaaand... OPEN!

About
This repository contains my CPP Module 03 exercises completed at 42 Bangkok. This module introduces class inheritance in C++, building on the Orthodox Canonical Form established in Module 02. The exercises progress from a simple base class to a diamond inheritance problem .

All code compiles with the C++98 standard and -Wall -Wextra -Werror.

Project Structure
text
.
├── ex00/
│   ├── Makefile
│   ├── ClapTrap.hpp
│   ├── ClapTrap.cpp
│   └── main.cpp
├── ex01/
│   ├── Makefile
│   ├── ClapTrap.hpp
│   ├── ClapTrap.cpp
│   ├── ScavTrap.hpp
│   ├── ScavTrap.cpp
│   └── main.cpp
├── ex02/
│   ├── Makefile
│   ├── ClapTrap.hpp / .cpp
│   ├── ScavTrap.hpp / .cpp
│   ├── FragTrap.hpp
│   ├── FragTrap.cpp
│   └── main.cpp
├── ex03/
│   ├── Makefile
│   ├── ClapTrap.hpp / .cpp
│   ├── ScavTrap.hpp / .cpp
│   ├── FragTrap.hpp / .cpp
│   ├── DiamondTrap.hpp
│   ├── DiamondTrap.cpp
│   └── main.cpp
└── README.md
Environment & Compilation
Requirements:

Unix-like system (Linux / macOS)

c++ (or g++) with C++98 support

make

Compile each exercise:

bash
cd ex00 && make
cd ex01 && make
cd ex02 && make
cd ex03 && make
Clean:

bash
make clean    # remove object files
make fclean   # remove object files and the executable
make re       # fclean + all
Exercises
ex00 — ClapTrap
Goal: Create a base class ClapTrap that will be inherited from in later exercises .

Requirements (OCCF):

Private members: Name, Hit points (10), Energy points (10), Attack damage (0).

Default constructor, copy constructor, copy assignment operator, destructor.

void attack(const std::string& target);

void takeDamage(unsigned int amount);

void beRepaired(unsigned int amount);

Behavior:

Attacking and repairing cost 1 energy point each.

A ClapTrap cannot act if it has 0 hit points or 0 energy points.

All actions print a descriptive message.

Concepts: Base class design, OCCF, resource management.

ex01 — ScavTrap
Goal: Create ScavTrap, a derived class that inherits from ClapTrap .

Requirements (OCCF):

Inherits constructors and destructor from ClapTrap.

Constructor and destructor must print specific messages (different from ClapTrap).

Hit points = 100, Energy points = 50, Attack damage = 20.

void attack(const std::string& target); — overrides ClapTrap::attack.

void guardGate(); — new member function.

Concepts: Public inheritance, constructor/destructor chaining, function overriding.

ex02 — FragTrap
Goal: Create FragTrap, another derived class from ClapTrap .

Requirements (OCCF):

Same OCCF structure as ScavTrap.

Hit points = 100, Energy points = 100, Attack damage = 30.

void highFivesGuys(void); — new member function.

Concepts: Multiple derived classes from the same base, consistent inheritance patterns.

ex03 — DiamondTrap
Goal: Solve the diamond inheritance problem by creating DiamondTrap, which inherits from both ScavTrap and FragTrap .

Requirements (OCCF):

DiamondTrap inherits from both ScavTrap and FragTrap (both of which inherit from ClapTrap).

Use virtual inheritance to avoid duplicate ClapTrap subobjects.

Private std::string _name (shadowing ClapTrap::_name).

Hit points = FragTrap's (100), Energy points = ScavTrap's (50), Attack damage = FragTrap's (30).

void whoAmI(); — displays both DiamondTrap::_name and ClapTrap::_name.

attack() should use ScavTrap::attack().

Concepts: Multiple inheritance, virtual inheritance, the diamond problem, name shadowing.

What I Learned
Inheritance: How derived classes inherit members from a base class and how constructors/destructors chain.

Function overriding: Redefining a base class method in a derived class.

Virtual inheritance: Solving the diamond problem by ensuring only one ClapTrap subobject exists in DiamondTrap.

Constructor/destructor order: Base class constructors run before derived ones; destructors run in reverse order.

OCCF in inheritance: Copy constructors and assignment operators must properly handle base class state.

C++98 compliance: No override keyword, no final, no nullptr.

Testing
Each exercise includes a main.cpp that demonstrates the required functionality.

Common checks:

ex00: Energy and hit points decrease correctly; no action when HP or EP is 0.

ex01: ScavTrap has correct stats and guardGate() works.

ex02: FragTrap has correct stats and highFivesGuys() works.

ex03: DiamondTrap has only one ClapTrap subobject (virtual inheritance); whoAmI() displays both names correctly.

Notes
This project is a personal learning record. It is not guaranteed to pass the Moulinette. If you are also at 42 Bangkok, try implementing it yourself first.

References
42 Bangkok official CPP Module 03 subject (Intra)

C++ Inheritance — cppreference

Virtual Inheritance — cppreference


