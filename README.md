#include <iostream>
#include <string>
#include <map>
#include <algorithm>

std::string to_lower(std::string str) {
    std::transform(str.begin(), str.end(), str.begin(), ::tolower);
    return str;
}

int main() {
    std::map<std::string, std::string> responses = {
        {"hello", "Hi there!"},
        {"how are you", "I'm doing well, thank you!"},
        {"bye", "Goodbye!"},
        {"", "I'm sorry, I didn't understand that."}
    };

    std::cout << "AI Chatbot: Hello! How can I help you?\n";
    while (true) {
        std::string user_input;
        std::cout << "You: ";
        std::getline(std::cin, user_input);

        user_input = to_lower(user_input);
        if (responses.find(user_input) != responses.end()) {
            std::cout << "AI Chatbot: " << responses[user_input] << "\n";
        } else {
            std::cout << "AI Chatbot: " << responses[""] << "\n";
        }

        if (user_input == "bye") {
            break;
        }
    }

    return 0;
}
