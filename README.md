# S3-Jamela-Rose-Alcantara

    #include <iostream>
    #include <string>
    #include <array>
    #include <algorithm>
    using namespace std;

    //variables
    bool drinkCorT(); //coffee or tea
    int drinkFlav(bool drinkType); //drink type

    int main()
    {
        cout << "Welcome to our Coffee Shop! The menu is displayed below.\n\n";

        string menu[4][4] = //menu array
        {
            {"Coffee", "   Price (AED)", "Tea", "   Price (AED)" },
            {"Ice Coffee", "3", "Ice Tea ", "3" },
            {"Milk Coffee", "2", "Milk Tea", "2" },
            {"Black Coffee", "1", "Black Tea", "1" },
        };

        for (int i = 0; i < 4; i++) //prints the menu by rows and columns
        {
            for (int j{ 0 }; j < 4; j++) {
                cout << menu[i][j] << "\t\t"; //\t for tab space
            }
            cout << endl;
        }

        int total = drinkFlav(drinkCorT());
        int usermoney;

        string sugar;

        cout << "\nIII. SUGAR\nWould you like to add some sugar? (Y for Yes, N for No): "; //ask the user if they want sugar or not
        getline(cin, sugar);
        while (!(sugar == "y" || sugar == "Y" || sugar == "n" || sugar == "N"))
        {
            cout << "\nInvalid input. Please choose between Y or N.\nWould you like to add some sugar? ";
            getline(cin, sugar);
        }
        if (sugar == "y" || sugar == "Y")
        {
            cout << "Sugar is added." << endl;
        }
        else if (sugar == "n" || sugar == "N")
        {
            cout << "No sugar is added." << endl;
        }

        //receipt
        cout << "\n\n* * * * * * * * * *\n   R E C E I P T\n* * * * * * * * * *\nTotal Amount: " << total << " AED " << "\nCash: ";
        cin >> usermoney;

        while (cin.fail())
        {
            cout << "\nError.\nPlease enter a valid input: ";
            cin.clear();
            cin.ignore(1000, '\n');
            cin >> usermoney;
        }
        while (cin.fail() || usermoney < total)
        {
            cout << "\nError. Not enough balance.\nPlease enter an enough amount: ";
            cin.clear();
            cin.ignore(1000, '\n');
            cin >> usermoney;
        }

        if ((usermoney - total) > 0 || (usermoney - total == 0))
        {
            cout << "- - - - - - - - - -\nChange: " << (usermoney - total) << " AED" << endl;
        }

        cout << "* * * * * * * * * *\n\nThank you! enjoy your drink." << endl;

    }

    bool drinkCorT() //asks the user to input their selected drink
    {

        string CorT{};

        cout << "\nI. DRINK SELECTION\nCoffee or Tea? ";
        getline(cin, CorT);

        while (!(CorT == "coffee" || CorT == "Coffee" || CorT == "tea" || CorT == "Tea")) //handles capitalization
        {
            cout << "\nInvalid input. Please choose between the given choices.\nChoose your drink between Coffee or Tea: ";
            getline(cin, CorT);
        }

        if (CorT == "coffee" || CorT == "Coffee")
        {
            return true;
        }
        else if (CorT == "tea" || CorT == "Tea")
        {
            return false;
        }
    }

    int drinkFlav(bool drinkType) //asks the user to input the drink type they would like
    {
        string flav;
        char function;

        if (drinkType) //coffee choices
        {
            cout << "\nII. DRINK TYPE\nChoose a type of drink from the given choices\n- Ice Coffee\n- Milk Coffee\n- Black Coffee\n\nType of Drink: ";
            getline(cin, flav);
            transform(flav.begin(), flav.end(), flav.begin(), ::tolower); //handles capitalization by converting a given character to lowercase
            while (!(flav == "ice coffee" || flav == "milk coffee" || flav == "black coffee")) //while not equal to
            {
                cout << "\nInvalid input.\nPlease choose between the three 3 choices (Ice Coffee, Milk Coffee, or Black Coffee): ";
                getline(cin, flav);
                transform(flav.begin(), flav.end(), flav.begin(), ::tolower);
            }
        }

        else //tea choices
        {
            cout << "\nII. DRINK TYPE\nChoose a type of drink from the given choices\n- Ice Tea\n- Milk Tea\n- Black Tea\n\nType of Drink: ";
            getline(cin, flav);
            transform(flav.begin(), flav.end(), flav.begin(), ::tolower); //handles capitalization by converting a given character to lowercase
            while (!(flav == "ice tea" || flav == "milk tea" || flav == "black tea")) //while not equal to
            {
                cout << "\nInvalid input.\nPlease choose between the 3 choices (Ice Tea, Milk Tea, or Black Tea): ";
                getline(cin, flav);
                transform(flav.begin(), flav.end(), flav.begin(), ::tolower);
            }
        }

        function = flav.at(0); //returns the code

        switch (function) //returns the flow of the execution to the function by switch
        {
        case 'i': {
            return 3;
            break; //used to terminate the loop
        }
        case 'j': {
            return 2;
            break;
        }
        case 'k': {
            return 1;
            break;
        }
        }

    }
