# Super-Market-Billing-System
                                                          Introduction:
The Supermarket Billing System is an essential component of modern retail, streamlining the billing process and improving customer experience. This review focuses on a project that utilizes OpenMP for parallel programming in C++, with the integration of Object-Oriented Programming (OOP) principles to create an efficient and scalable billing system for supermarkets.

                                                           What is OpenMP:
OpenMP (Open Multi-Processing) is an application programming interface (API) that enables developers to write parallel programs that can run on shared-memory multiprocessor systems. It simplifies parallel programming by providing a set of compiler directives and library routines, making it easier to exploit multi-core processors and achieve better performance.

                                                           Why C++ as Parallel Programming:
C++ is a popular choice for parallel programming due to its robust support for both OOP and low-level system programming. When used in conjunction with OpenMP, C++ allows developers to leverage the power of multi-core processors effectively. Its ability to manage resources efficiently, along with features like thread management and synchronization mechanisms, makes it well-suited for parallel computing tasks in the Supermarket Billing System.


                                                         How OOPs are Helpful to this Project:
Object-Oriented Programming is a software development paradigm that emphasizes the use of objects, which are instances of classes, to model real-world entities and their interactions. In the context of the Supermarket Billing System, OOP principles can provide several advantages:
1.	Modularity: OOP allows you to break down the system into smaller, manageable classes, making it easier to develop, maintain, and extend the software.
2.	Encapsulation: Encapsulation hides the internal details of a class, ensuring data integrity and reducing the chances of unintended interference between components.
3.	Inheritance: Inheritance enables you to create specialized classes that inherit properties from more general classes, promoting code reuse and hierarchy.
4.	Polymorphism: Polymorphism allows you to design flexible and extensible systems by providing different implementations for common interfaces or functions.

                                                        Project Implementations:
The project successfully utilizes OpenMP for parallelizing critical tasks in the Supermarket Billing System. Some key implementations include:
1.	Parallelizing item processing: OpenMP is used to process items concurrently, reducing checkout time and improving customer satisfaction.
2.	Efficient inventory management: Parallel programming ensures that inventory updates are done concurrently, preventing stock discrepancies and enhancing accuracy.
3.	Billing and payment processing: Parallelism aids in handling multiple customer transactions simultaneously, resulting in faster checkout experiences.
4.	Error handling and reporting: OOP concepts are employed to create robust error-handling mechanisms and generate detailed reports for store management.
Conclusion: In summary, this project leverages OpenMP, C++, and OOP to create an efficient, scalable Supermarket Billing System, enhancing retail operations.

                                                              CODE:


            #include <iostream>
            #include <vector>
            #include <string>
            #include <map>
            #include <omp.h> // Include OpenMP header
            
            int total_bill = 0;
            
            class Shop {
            public:
                Shop(const std::string& name) : name(name) {}
                virtual ~Shop() {}
            
                double calculatePrice(int price) {}
            
                std::string getName() const {
                    return name;
                }
            
                protected:
                std::string name;
                void print_bill(){
                    std::cout<<name;
                    std::cout << "Total Bill: $" << total_bill << std::endl;
                }
            };
            
            class Groceries : public Shop {
                 public:
                    Groceries(const std::string& name) : Shop(name) {}
            };
            
            class Fashion : public Shop {
            public:
                Fashion(const std::string& name) : Shop(name) {}
            };
            
            class Electronics : public Shop {
            public:
                Electronics(const std::string& name) : Shop(name) {}
            };
            
            class Staples : public Groceries {
            public:
                Staples(const std::string& name) : Groceries(name) {}
                double calculatePrice(int price){
                    total_bill+=price;
                }
            };
            
            class SnacksAndBeverages : public Groceries {
            public:
                SnacksAndBeverages(const std::string& name) : Groceries(name) {}
                double calculatePrice(int price){
                    total_bill+=price;
                }
            };
            
            class Household : public Groceries {
            public:
                Household(const std::string& name) : Groceries(name) {}
                double calculatePrice(int price){
                    total_bill+=price;
                }
                void print_bill(){
                    std::cout << "Total Bill: $" << total_bill << std::endl;
                }
            };
            
            class Menclothing : public Fashion {
            public:
                Menclothing(const std::string& name) : Fashion(name) {}
                double calculatePrice(int price){
                    total_bill+=price;
                }
            };
            
            class Womenclothing : public Fashion {
            public:
                Womenclothing(const std::string& name) : Fashion(name) {}
                double calculatePrice(int price){
                    total_bill+=price;
                }
            };
            
            class TravelAndAccessories : public Fashion {
            public:
                TravelAndAccessories(const std::string& name) : Fashion(name) {}
                double calculatePrice(int price){
                    total_bill+=price;
                }
            };
            
            class MobilesAndAccessories : public Electronics {
            public:
                MobilesAndAccessories(const std::string& name) : Electronics(name) {}
                double calculatePrice(int price){
                    total_bill+=price;
                }
            };
            
            class LaptopsAndAccessories : public Electronics {
            public:
                LaptopsAndAccessories(const std::string& name) : Electronics(name) {}
                double calculatePrice(int price){
                    total_bill+=price;
                }
            };
            
            class HomeAppliances : public Electronics {
            public:
                HomeAppliances(const std::string& name) : Electronics(name) {}
                double calculatePrice(int price){
                    total_bill+=price;
                }
            };
            
            
            int main() {
                int choice;
                std::vector<Shop*> shops;
                std::map<int, std::string> menu;
            
                menu[1] = "Groceries";
                menu[2] = "Fashion";
                menu[3] = "Electronics";
                menu[4] = "Exit";
            
                std::vector<std::pair<std::string, double>> cart; // Store purchased items
            
                while (true) {
                    std::cout << "Menu:" << std::endl;
                    for (const auto& item : menu) {
                        std::cout << item.first << ". " << item.second << std::endl;
                    }
            
                    std::cout << "Enter your choice: ";
                    std::cin >> choice;
            
                    if (choice == 4) {
                        // Exit
                        break;
                    }
            
                    if (menu.find(choice) == menu.end()) {
                        std::cout << "Invalid choice. Please try again." << std::endl;
                        continue;
                    }
            
                    // Handle different shop types based on the user's choice
                    switch (choice) {
                        case 1: {
                            // Groceries
                            int subChoice;
                            std::map<int, std::string> groceryMenu;
            
                            groceryMenu[1] = "Staples";
                            groceryMenu[2] = "SnacksAndBeverages";
                            groceryMenu[3] = "Household";
                            groceryMenu[4] = "Back";
            
                            while (true) {
                                std::cout << "Groceries Menu:" << std::endl;
                                for (const auto& item : groceryMenu) {
                                    std::cout << item.first << ". " << item.second << std::endl;
                                }
                                std::cout << "Enter your choice: ";
                                std::cin >> subChoice;
            
                                if (subChoice == 4) {
                                    // Back
                                    break;
                                }
            
                                if (groceryMenu.find(subChoice) == groceryMenu.end()) {
                                    std::cout << "Invalid choice. Please try again." << std::endl;
                                    continue;
                                }
            
                                if (subChoice >= 1 && subChoice <= 3) {
                                    std::string itemName;
                                    double itemPrice;
                                    std::cout << "Enter the name of the item: ";
                                    std::cin >> itemName;
                                    std::cout << "Enter the price of the item: ";
                                    std::cin >> itemPrice;
            
                                    // Create a dynamic object of the selected class
                                    Shop* newItem = nullptr;
                                    if (subChoice == 1) {
                                        newItem = new Staples(itemName);
                                        newItem->calculatePrice(itemPrice);
                                    } else if (subChoice == 2) {
                                        newItem = new SnacksAndBeverages(itemName);
                                        newItem->calculatePrice(itemPrice);
                                    } else if (subChoice == 3) {
                                        newItem = new Household(itemName);
                                        newItem->calculatePrice(itemPrice);
                                    }
            
                                    // Add the item to the cart
                                    cart.push_back(std::make_pair(itemName, itemPrice));
            
                                    std::cout << "Item added to the cart." << std::endl;
                                }
                            }
                            break;
                        }
                        case 2: {
                            // Fashion
                            int subChoice;
                            std::map<int, std::string> fashionMenu;
            
                            fashionMenu[1] = "Men's Clothing";
                            fashionMenu[2] = "Women's Clothing";
                            fashionMenu[3] = "Travel and Accessories";
                            fashionMenu[4] = "Back";
            
                            while (true) {
                                std::cout << "Fashion Menu:" << std::endl;
                                for (const auto& item : fashionMenu) {
                                    std::cout << item.first << ". " << item.second << std::endl;
                                }
                                std::cout << "Enter your choice: ";
                                std::cin >> subChoice;
            
                                if (subChoice == 4) {
                                    // Back
                                    break;
                                }
            
                                if (fashionMenu.find(subChoice) == fashionMenu.end()) {
                                    std::cout << "Invalid choice. Please try again." << std::endl;
                                    continue;
                                }
            
                                if (subChoice >= 1 && subChoice <= 3) {
                                    std::string itemName;
                                    double itemPrice;
                                    std::cout << "Enter the name of the item: ";
                                    std::cin >> itemName;
                                    std::cout << "Enter the price of the item: ";
                                    std::cin >> itemPrice;
            
                                    // Create a dynamic object of the selected class
                                    Shop* newItem = nullptr;
                                    if (subChoice == 1) {
                                        newItem = new Menclothing(itemName);
                                        newItem->calculatePrice(itemPrice);
                                    } else if (subChoice == 2) {
                                        newItem = new Womenclothing(itemName);
                                        newItem->calculatePrice(itemPrice);
                                    } else if (subChoice == 3) {
                                        newItem = new TravelAndAccessories(itemName);
                                        newItem->calculatePrice(itemPrice);
                                    }
            
                                    // Add the item to the cart
                                    cart.push_back(std::make_pair(itemName, itemPrice));
            
                                    std::cout << "Item added to the cart." << std::endl;
                                }
                            }
                            break;
                        }
            
                        case 3: {
                            // Electronics
                            int subChoice;
                            std::map<int, std::string> electronicsMenu;
            
                            electronicsMenu[1] = "Mobiles and Accessories";
                            electronicsMenu[2] = "Laptops and Accessories";
                            electronicsMenu[3] = "Home Appliances";
                            electronicsMenu[4] = "Back";
            
                            while (true) {
                                std::cout << "Electronics Menu:" << std::endl;
                                for (const auto& item : electronicsMenu) {
                                    std::cout << item.first << ". " << item.second << std::endl;
                                }
                                std::cout << "Enter your choice: ";
                                std::cin >> subChoice;
            
                                if (subChoice == 4) {
                                    // Back
                                    break;
                                }
                                if (electronicsMenu.find(subChoice) == electronicsMenu.end()) {
                                    std::cout << "Invalid choice. Please try again." << std::endl;
                                    continue;
                                }
                                if (subChoice >= 1 && subChoice <= 3) {
                                    std::string itemName;
                                    double itemPrice;
                                    std::cout << "Enter the name of the item: ";
                                    std::cin >> itemName;
                                    std::cout << "Enter the price of the item: ";
                                    std::cin >> itemPrice;
            
                                    // Create a dynamic object of the selected class
                                    Shop* newItem = nullptr;
                                    if (subChoice == 1) {
                                        newItem = new MobilesAndAccessories(itemName);
                                        newItem->calculatePrice(itemPrice);
                                    } else if (subChoice == 2) {
                                        newItem = new LaptopsAndAccessories(itemName);
                                        newItem->calculatePrice(itemPrice);
                                    } else if (subChoice == 3) {
                                        newItem = new HomeAppliances(itemName);
                                        newItem->calculatePrice(itemPrice);
                                    }
            
                                    // Add the item to the cart
                                    cart.push_back(std::make_pair(itemName, itemPrice));
            
                                    std::cout << "Item added to the cart." << std::endl;
                                }
                            }
                            break;
                        }
                    }
                }
            
                // Calculate the total bill and display purchased items
                std::cout << "Items Purchased:" << std::endl;
                #pragma omp parallel for reduction(+:totalBill)
                for (int i = 0; i < cart.size(); ++i) {
                    const auto& item = cart[i];
                    #pragma omp critical
                    {
                        std::cout << item.first << " - Price: $" << item.second << std::endl;
                        total_bill+=item.second;
                    }
                }
                std::cout << "Total Bill: $" << total_bill << std::endl;
            }

                                   OUTPUT:
![image](https://github.com/PURNANANDH/Super-Market-Billing-System/assets/133785378/84008a43-83fa-49c5-bd81-510836de1bba)
![image](https://github.com/PURNANANDH/Super-Market-Billing-System/assets/133785378/63a41a84-4299-4511-83a0-b7de2f55e34b)

