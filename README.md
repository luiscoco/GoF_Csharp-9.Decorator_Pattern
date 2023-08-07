# GoF_Csharp-Decorator_Pattern

Adds additional behaviors or responsibilities to objects dynamically, without affecting other objects.

```csharp
﻿// Creating a simple coffee
ICoffee simpleCoffee = new SimpleCoffee();
Console.WriteLine("Simple Coffee: " + simpleCoffee.GetDescription() + " - Cost: $" + simpleCoffee.GetCost());

// Adding milk to the coffee
ICoffee coffeeWithMilk = new MilkDecorator(simpleCoffee);
Console.WriteLine("Coffee with Milk: " + coffeeWithMilk.GetDescription() + " - Cost: $" + coffeeWithMilk.GetCost());

// Adding caramel to the coffee
ICoffee coffeeWithCaramel = new CaramelDecorator(simpleCoffee);
Console.WriteLine("Coffee with Caramel: " + coffeeWithCaramel.GetDescription() + " - Cost: $" + coffeeWithCaramel.GetCost());

// Adding both milk and caramel to the coffee
ICoffee coffeeWithMilkAndCaramel = new CaramelDecorator(new MilkDecorator(simpleCoffee));
Console.WriteLine("Coffee with Milk and Caramel: " + coffeeWithMilkAndCaramel.GetDescription() + " - Cost: $" + coffeeWithMilkAndCaramel.GetCost());

public interface ICoffee
{
    string GetDescription();
    double GetCost();
}

public class SimpleCoffee : ICoffee
{
    public string GetDescription()
    {
        return "Simple coffee";
    }

    public double GetCost()
    {
        return 2.0;
    }
}

// MilkDecorator adds milk to the coffee
public class MilkDecorator : ICoffee
{
    private readonly ICoffee _coffee;

    public MilkDecorator(ICoffee coffee)
    {
        _coffee = coffee;
    }

    public string GetDescription()
    {
        return _coffee.GetDescription() + ", with milk";
    }

    public double GetCost()
    {
        return _coffee.GetCost() + 1.0;
    }
}

// CaramelDecorator adds caramel to the coffee
public class CaramelDecorator : ICoffee
{
    private readonly ICoffee _coffee;

    public CaramelDecorator(ICoffee coffee)
    {
        _coffee = coffee;
    }

    public string GetDescription()
    {
        return _coffee.GetDescription() + ", with caramel";
    }

    public double GetCost()
    {
        return _coffee.GetCost() + 1.5;
    }
}
```

## How to setup github actions

![Csharp Github actions](https://github.com/luiscoco/GoF_Csharp-9.Decorator_Pattern/assets/32194879/f8170e84-3f28-4075-aa51-fc9c3e13474d)
