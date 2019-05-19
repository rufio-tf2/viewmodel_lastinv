# Viewmodel + lastinv

- [Viewmodel + lastinv](#viewmodel--lastinv)
  - [Install](#install)
  - [Control viewmodels for individual classes](#control-viewmodels-for-individual-classes)
    - [Example: Soldier, Slot 1](#example-soldier-slot-1)
    - [Example: Demoman, Slot 2](#example-demoman-slot-2)
  - [Philosophy](#philosophy)
  - [API](#api)

**Note:** This script rebinds the <kbd>1</kbd>-<kbd>5</kbd> keys, and the <kbd>Q</kbd> key to use this script's custom commands.

## Install

1. [Download](https://github.com/rufio-tf2/viewmodel_lastinv/archive/master.zip) this ZIP. Extract it. Find the inner `vm_lastinv` folder.
1. Drag the `vm_lastinv` folder into your `custom/YOUR_CONFIG/cfg` folder (replace `YOUR_CONFIG` with the name of your config).
1. Wire it into your `autoexec.cfg`:

   ```go
   // autoexec.cfg
   exec vm_lastinv/init
   ```

1. Use default settings as starting point for all classes. In your base class settings (`reset.cfg`, or whatever you've called it):

   ```go
   // reset.cfg
   exec vm_lastinv/default-slot-settings
   ```

   > _[What is `reset.cfg`?](https://youtu.be/a8yKrKD1EJg)_

## Control viewmodels for individual classes

### Example: Soldier, Slot 1

Imagine that I want the Soldier's viewmodel to be **off** for his primary weapon, the first slot. By default, the `CUSTOM_slot1` command (when I press <kbd>1</kbd>) is:

```go
alias CUSTOM_slot1 "slot1; viewmodelOn;"
```

I need to change that so that it turns the viewmodel off instead.

In the `soldier.cfg` file, I'll add these lines **after I execute `reset.cfg`**:

```go
// soldier.cfg
exec reset // Always the first line

alias CUSTOM_slot1 "slot1; viewmodelOff;" // Add this
viewmodelOff // Add this to initialize for slot1
```

Because it's the first slot, I also need to initialize the viewmodel to be off, because it's the default slot. If I were turning the viewmodel off for any other slot, then I wouldn't need to do that.

### Example: Demoman, Slot 2

If I want to turn off the viewmodel for Demoman's second slot, in his file I'd add:

```go
// demoman.cfg
exec reset // Always the first line

alias CUSTOM_slot2 "slot2; viewmodelOff;" // Add this
```

Here I don't want to initialize the viewmodel to being off, because I'm leaving his viewmodel for slot 1 on.

## Philosophy

1.  Anywhere you would use the TF2 slot commands -- `slot1`, `slot2`, ..., `slot5` -- instead use this script's custom slot commands:

    ```go
    bind 1 CUSTOM_slot1
    bind 2 CUSTOM_slot2
    bind 3 CUSTOM_slot3
    bind 4 CUSTOM_slot4
    bind 5 CUSTOM_slot5
    ```

2.  Instead of using TF2's `r_drawviewmodel` console command, use this script's two custom commands:

    - `viewmodelOn`
    - `viewmodelOff`

3.  Instead of TF2's `lastinv` command use this script's `vm_lastinv`:

    ```go
    bind Q vm_lastinv
    ```

## API

| Custom Command | TF2 Command         |
| -------------- | ------------------- |
| `vm_lastinv`   | `lastinv`           |
| `viewmodelOn`  | `r_drawviewmodel 1` |
| `viewmodelOff` | `r_drawviewmodel 0` |
| `CUSTOM_slot1` | `slot1`             |
| `CUSTOM_slot2` | `slot2`             |
| `CUSTOM_slot3` | `slot3`             |
| `CUSTOM_slot4` | `slot4`             |
| `CUSTOM_slot5` | `slot5`             |
