
# Garry's Mod Hook Tutorial

This tutorial provides an introduction to using hooks in Garry's Mod addons. Hooks are a powerful way to interact with and modify game events and functionality.

## What Are Hooks?

Hooks in Garry's Mod allow you to "hook" into specific events or functions in the game's code. This enables you to execute custom code when those events occur, providing a way to modify gameplay, add new features, or enhance existing ones.

## Basic Hook Example

Let's start with a simple example from our `MyAddon` template, where we make hamburgers vanish when placed in an oven.

### Creating the Hook

In the `lua/autorun/myaddon.lua` file of your addon, we define a hook using `hook.Add`. Here's how it looks:

hook.Add("Think", "CheckHamburgerInOven", function()
    local hamburger = ents.FindByName("hamburger_prop_name")[1]
    local oven = ents.FindByName("oven_prop_name")[1]
    
    if IsValid(hamburger) and IsValid(oven) and hamburger:GetPos():Distance(oven:GetPos()) < 10 then
        hamburger:Remove()
    end
end)



In this example:
- We use the `"Think"` event, which runs every frame.
- We provide a unique identifier `"CheckHamburgerInOven"` for the hook.
- The provided function is executed when the hook is triggered.

### Explaining the Hook

- We find the hamburger and oven entities in the game using `ents.FindByName`.
- We check if both entities are valid and if the hamburger is close enough to the oven (within 10 units).
- If the conditions are met, we remove the hamburger entity from the game using `hamburger:Remove()`.

## Advanced Hook Usage

Hooks can be used for a wide range of purposes in Garry's Mod addons. You can hook into various game events, such as player actions, entity creation, damage events, and more. By doing so, you can create complex and interactive addons.

For more advanced usage and a comprehensive list of available hooks, refer to the [Garry's Mod Wiki - Hooks](https://wiki.facepunch.com/gmod/Hooks).

## Conclusion

Hooks are a fundamental part of Garry's Mod addon development, allowing you to customize and extend the game's functionality. With this basic understanding, you can begin exploring and experimenting with hooks to create your own unique addons.

If you have any questions or need further assistance, feel free to reach out on our [GitHub repository](https://github.com/yourusername/your-repo).

Happy addon development!

