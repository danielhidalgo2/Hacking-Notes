## SENSITIVE DOCUMENTS

site:example.com (ext:doc OR ext:docx OR ext:odt OR ext:pdf OR ext:rtf OR ext:ppt OR ext:pptx OR ext:csv OR ext:xls OR ext:xlsx OR ext:txt OR ext:xml OR ext:json OR ext:zip OR ext:rar OR ext:md OR ext:log OR ext:bak OR ext:conf OR ext:sql)


## SQLI ERRORS

site:example.com intext:"sql syntax near" OR intext:"syntax error" OR intext:"unexpected end of SQL" OR intext:"Warning: mysql_" OR intext:"pg_connect()" OR intext:"error in your SQL syntax" OR intext:"OLE DB Provider for SQL Server"

## OPEN REDIRECTS

inurl:redirectUrl=http site:example.com:inurl:redir | inurl:url | inurl:redirect | inurl:return | inurl:src=http | inurl:r=http

https://taksec.github.io/google-dorks-bug-bounty/