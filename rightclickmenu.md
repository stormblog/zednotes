
You must hit the *Control* button to simulate activating a `right click.`

```rust
rg right_click_menu
```

Right click menus are used in
- workspace/src/dock.rs
- workspace/src/pane.rs

You find *right click menus* in Zed in two key places

They are on the editor tabs at the top of the screen and provide some interesting functionality including closing tabs that are to right or the left along with closing all of the tabs etc...

They are on the status bar buttons at the bottom of the screen including the

- assistant panel
- chat panel
- collab panel
- terminal panel

In dock.rs the menu can have the following states

```rust
const POSITIONS: [DockPosition; 3] = [
     DockPosition::Left,
     DockPosition::Right,
     DockPosition::Bottom,
 ];
```

As I begin to understand this concept better you will see that as you select
the different states they move around in the status bar from the right to the
left and in the case of terminal to the right for *bottom*.

### Kallax

The reason I got turned on to this idea in the first place is because an old version of Kallax
used overlays which are now called [anchored](https://github.com/zed-industries/zed/blob/main/crates/gpui/src/elements/anchored.rs).

Anchored is used in Kallax as a dropdown to both *play* and *queue* a track.

This zed commit point is what Kallax used to use in its Cargo.lock where the
old overlays work fine.

```rust
gco 4dc61f7ccd6ac77a6f03d90d7ee80e855b0f32b9
```

This is where you land if you check out the above commit point...

https://github.com/zed-industries/zed/tree/4dc61f7ccd6ac77a6f03d90d7ee80e855b0f32b9

This PR is where overlay was renamed to anchored: [Rework overlay element](https://github.com/zed-industries/zed/pull/9911)

### References

- [right_click_menu.rs history](https://github.com/zed-industries/zed/commits/main/crates/ui/src/components/right_click_menu.rs)
- [right click menus are built with ContextMenus](https://github.com/zed-industries/zed/blob/main/crates/ui/src/components/context_menu.rs)
- Kallax uses [ContextMenus](https://github.com/Ben-Wormald/kallax/blob/main/src/views/context_menu.rs) as noted above and because I didn't understand what it was I renamed it to `Dropdown` when I refactored Kallax early on...
