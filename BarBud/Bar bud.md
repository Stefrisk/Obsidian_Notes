mermaid chart test 

flowchart TD
    style Home fill:#7e6fff,stroke:#333,stroke-width:2px,color:#fff
    style Recipes fill:#3dcb6c,stroke:#333,stroke-width:2px,color:#fff
    style Ingredients fill:#ffb545,stroke:#333,stroke-width:2px,color:#fff

    Home["Home Page"]
    Recipes["Recipes Page"]
    Ingredients["Ingredients Page"]

    Home --> Recipes
    Home --> Ingredients
    Recipes --> Ingredients
    Ingredients --> Recipes

