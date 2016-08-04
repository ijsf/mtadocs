This class can be found at **mtasa-blue\\MTA10\_Server\\mods\\deathmatch\\logic\\CAccountPassword.cpp**.

Valid password types
--------------------

There are two different supported password types right now:

-   **md5**: directly stores the md5 hash of the password *(deprecated)*
-   **sha256**: stores the sha256 hash, the type of password, and the salt

<!-- -->

    m_strSha256 (64) + m_strType (1) + m_strSalt (32);

-   **m\_strSha256**: generated string (64 characters; 00-64)
-   **m\_strType**: differentiates between password type (1 character; 65th character)
-   **m\_strSalt**: regular salt (32 characters; 66-97)

### md5 string generation

When **m\_strType = 1**, the legacy md5 mode is used.

    strMd5 = md5(strPlaintextPassword).UPPERCASE
    m_strSha256 = sha256(m_strSalt + strMd5)

### sha256 string generation

When **m\_strType = 0**, the legacy md5 mode is NOT used and the plaintext password has been directly hashed.

    m_strSha256 = sha256(m_strSalt + strPlaintextPassword)
