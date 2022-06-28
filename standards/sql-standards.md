# SQL Standards

SQL comes in a variety of flavours; writing a standards guide for each of them
would result in an entire page on its own. For this reason, we had an
engineering day at our company in 2022 that tasked a team with investigating the
best way for us to keep SQL writing concise and in a way that should not cause
formatting issues and arguments in merge requests. The resulted in a Shed
specific set of rules that plug and play nicely with the tool
[SQLFLUFF](https://www.sqlfluff.com/).

Add the configuration file called `sqlfluff.config` to your project directory or
somewhere referenced/linked to in your code editor of choice. The configuration
setting:

```toml
[sqlfluff]
verbose = 1
templater = jinja
exclude_rules = L003,L036,L039
output_line_length = 121
sql_file_exts=.sql

[sqlfluff:rules]
tab_space_size = 5
max_line_length = 250
indent_unit = space
comma_style = leading
allow_scalar = True
single_table_references = consistent
unquoted_identifiers_policy = aliases

[sqlfluff:rules:L010] # Keywords
capitalisation_policy = upper

[sqlfluff:rules:L014]
extended_capitalisation_policy = lower

[sqlfluff:rules:L030] # function names
capitalisation_policy = lower

[sqlfluff:rules:L052] # final semicolon
multiline_newline = True
```

Documentation for the [tool](https://docs.sqlfluff.com/en/stable/).
