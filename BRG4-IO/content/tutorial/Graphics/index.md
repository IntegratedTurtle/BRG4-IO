+++
title = 'Graphics'
date = 2024-11-02T20:56:50+01:00
draft = false
+++

Hier geht es einfach mal darum wie man simpel in c++ ein program compilieren can, welches einem Bilder rendert\
Ich werde hier bei sfml benutzen, da es sehr wenig braucht, man allerdings schon ein wenig damit machen kann.

# Install the library
Ich werde hier nur die detail dazu angeben wie man dies auf Linux macht, da ich hoffe, dass alle auf Windows, WSL2 laufen
## Ubuntu
```
sudo apt install libsfml-dev
```
## Fedora
```
sudo dnf install SFML-devel
```
## OpenSuse
```
sudo zypper in sfml2-devel
```

# Code
```
#include <SFML/Graphics.hpp>

int main()
{
    sf::RenderWindow window(sf::VideoMode(1080, 920), "SFML works!");
    sf::CircleShape shape(100.f);
    shape.setFillColor(sf::Color::Green);

    // Create a clock to measure time
    sf::Clock clock;

    while (window.isOpen())
    {
        sf::Event event;
        while (window.pollEvent(event))
        {
            if (event.type == sf::Event::Closed)
                window.close();
        }

        // Check if one second has passed
        if (clock.getElapsedTime().asSeconds() >= 1.0f)
        {
            // Update the shape size
            shape.setRadius(shape.getRadius() * 1.1);

            // Restart the clock to measure the next second
            clock.restart();
        }

        window.clear();
        window.draw(shape);
        window.display();
    }

    return 0;
}
```

# Compiling
```
g++ main.cpp -o main -lsfml-graphics -lsfml-window -lsfml-system
```
