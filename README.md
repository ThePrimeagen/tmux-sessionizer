# TMUX Sessionizer

A powerful utility script to streamline your tmux workflow by quickly creating, switching between, and managing project sessions.

## Features

- Quickly navigate between project directories
- Automatically create and name tmux sessions based on directory names
- Switch seamlessly between existing sessions
- Support for custom session initialization through `.tmux-sessionizer` files
- Robust error handling with helpful color-coded messages

## Installation

1. Save the script to a location in your `PATH`, for example:

```bash
cp tmux-sessionizer ~/.local/scripts/tmux-sessionizer
chmod +x ~/.local/scripts/tmux-sessionizer
```

2. Make sure the script's location is in your PATH variable.

## Usage

### Basic Usage

Simply run the script without arguments to select a project directory using fzf:

```bash
tmux-sessionizer
```

### Direct Session Creation

Specify a directory path directly:

```bash
tmux-sessionizer ~/dev/myproject
```

### Keyboard Shortcut (Recommended)

Add a keyboard shortcut in your `.zprofile` or `.zshrc` for quick access:

```bash
# Key bindings
bindkey -s ^f "tmux-sessionizer\n"  # Use Ctrl+f to launch
```

Press `Ctrl+f` anytime to activate the sessionizer.

## Custom Session Initialization

You can create a `.tmux-sessionizer` file in your project directory with custom commands to run when the session is created. This is useful for:

- Opening specific files
- Running development servers
- Setting up pane layouts

If no project-specific file is found, the script will try to use `~/.tmux-sessionizer` as a default.

## How It Works

1. If a directory is provided as an argument, it uses that; otherwise, it prompts you to select one using fzf
2. Creates a tmux session named after the directory (replacing dots with underscores)
3. If you're already in tmux, it switches to the specified session
4. If not in tmux, it attaches to the new session
5. Runs the appropriate `.tmux-sessionizer` file if available

## Customization

You can modify the search paths in the script to include your own project directories:

```bash
selected=$(find ~/dev ~/personal ~/work -mindepth 1 -maxdepth 1 -type d 2>/dev/null | fzf)
```

## Dependencies

- tmux
- fzf (for directory selection)
- bash
