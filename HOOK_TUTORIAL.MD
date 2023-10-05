# Garry's Mod Hook Tutorial

This tutorial provides an introduction to using hooks in Garry's Mod addons. Hooks are a powerful way to interact with and modify game events and functionality.

## What Are Hooks?

Hooks in Garry's Mod allow you to "hook" into specific events or functions in the game's code. This enables you to execute custom code when those events occur, providing a way to modify gameplay, add new features, or enhance existing ones.

## Basic Hook Example

Let's start with a simple example from our `MyAddon` template, where we make hamburgers vanish when placed in an oven.

### Creating the Hook

In the `lua/autorun/myaddon.lua` file of your addon, we define a hook using `hook.Add`. Here's how it looks:

```lua
hook.Add("Think", "CheckHamburgerInOven", function()
    local hamburger = ents.FindByName("hamburger_prop_name")[1]
    local oven = ents.FindByName("oven_prop_name")[1]
    
    if IsValid(hamburger) and IsValid(oven) and hamburger:GetPos():Distance(oven:GetPos()) < 10 then
        hamburger:Remove()
    end
end)

