# Free-Willy Agent Guidelines

## File Operations & Tooling
- **Dedicated File-Writing Tools:** Never use `cat << 'EOF'`, `cat << EOF`, or bash heredocs to write or edit files, as they stall on standard input. Always use dedicated file-writing tools (`write_to_file`, `replace_file_content`, `multi_replace_file_content`).
