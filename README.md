# CRX Police Customs

A simple highly optimized, feature-rich vehicle customization script designed specifically for Police and Emergency Service departments. Built on **ox_lib** and **ox_target**, this resource provides a clean, context-menu-based interface for modifying department vehicles with support for specialized police equipment (Aerials, ALPRs, Arch Covers).

## 🌟 Features

*   **Framework Agnostic:** Auto-detects **ESX** or **QBCore** (Bridge included).
*   **Optimized Performance:** Peds only spawn when a player enters the area (0.00ms idle).
*   **Deep Customization:**
    *   **Performance:** Granular upgrades (Engine, Brakes, Turbo, etc.) with "Stock" reversion.
    *   **Bodywork:** Auto-detects all visual mods including Bumpers, Fenders, Hoods, and Spoilers.
    *   **Police Specials:** Specific support for **Arch Covers**, **Aerials**, **Exterior Trim**, and **Searchlights**.
    *   **Lighting:** Full Xenon control (Colors & Toggles) plus Dashboard & Interior light colors.
    *   **Extras:** Toggleable menu for vehicle extras (Lightbars, Rammbars) with state detection.
    *   **Plates:** Change License Plate Text and Style (Blue/White, Black/Yellow, etc.).
*   **Smart Livery System:** Supports both standard GTA liveries and Modkit (Mod 48) liveries.
*   **Location Security:**
    *   Configurable locations.
    *   **Job Restrictions:** Restrict specific locations to specific departments (e.g., Sandy Shores for Sheriff only).
    *   **Duty Checks:** Automatically checks if QBCore players are "On Duty".

## 📦 Dependencies

This resource relies on the Overextended suite for its UI and targeting:

*   [ox_lib](https://github.com/overextended/ox_lib) (Interface & Logic)
*   [ox_target](https://github.com/overextended/ox_target) (Interaction)
*   *Framework:* `es_extended` OR `qb-core`

## 🚀 Installation

1.  **Download:** Place the `crx_policecustoms` folder into your server's `resources` directory.
2.  **Config:** Open `config.lua` to set up your workshop locations (see below).
3.  **Start:** Add the following to your `server.cfg` (ensure it starts **after** dependencies):
    ```cfg
    ensure ox_lib
    ensure ox_target
    ensure crx_policecustoms
    ```
   
## config.lua

```
Config = {}

-- The Ped model to spawn at the workshop
Config.PedModel = 's_m_y_cop_01'

Config.Locations = {
    {
        label = "Mission Row PD",
        coords = vector4(441.05, -981.56, 30.69, 90.0), -- X, Y, Z, Heading
        jobs = { "police", "lspd" } -- Jobs allowed to use THIS specific spot
    },
    {
        label = "Sandy Shores Sheriff",
        coords = vector4(1853.07, 3688.40, 34.27, 210.0),
        jobs = { "sheriff", "bcso" } -- Jobs allowed here
    },
    -- Add as many locations as you need...
}
```

Open config.lua to manage your locations. You can define which jobs have access to which specific workshop. 

Go On Duty: Ensure your character is clocked in (if using QBCore).
Enter Vehicle: Get into the police vehicle you wish to modify.
Drive to Location: Go to one of the points defined in your config.
Exit the vehicle (or stay inside if your target allows).
Hold Left Alt (Target Key) and look at the mechanic Ped.
Select "Modify Department Vehicle". 

Troubleshooting
Menu won't open? Ensure you are in a vehicle.
Ensure your job matches the jobs list for that specific location in config.lua.(QBCore)
Ensure you are /onduty."Unavailable" Messages?
The menu auto-hides categories (like Spoilers or Extras) if the specific car you are in does not support them. This is intended behavior to keep the menu clean.
