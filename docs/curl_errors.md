List of CURL Errors, updates can be found [here](http://curl.haxx.se/libcurl/c/libcurl-errors.html)

**CURLE\_OK (0)**

All fine. Proceed as usual.

**CURLE\_UNSUPPORTED\_PROTOCOL (1)**

The URL you passed to libcurl used a protocol that this libcurl does not support. The support might be a compile-time option that you didn't use, it can be a misspelled protocol string or just a protocol libcurl has no code for.

**CURLE\_FAILED\_INIT (2)**

Very early initialization code failed. This is likely to be an internal error or problem.

**CURLE\_URL\_MALFORMAT (3)**

The URL was not properly formatted.

**CURLE\_COULDNT\_RESOLVE\_PROXY (5)**

Couldn't resolve proxy. The given proxy host could not be resolved.

**CURLE\_COULDNT\_RESOLVE\_HOST (6)**

Couldn't resolve host. The given remote host was not resolved.

**CURLE\_COULDNT\_CONNECT (7)**

Failed to connect() to host or proxy.

**CURLE\_FTP\_WEIRD\_SERVER\_REPLY (8)**

After connecting to a FTP server, libcurl expects to get a certain reply back. This error code implies that it got a strange or bad reply. The given remote server is probably not an OK FTP server.

**CURLE\_REMOTE\_ACCESS\_DENIED (9)**

We were denied access to the resource given in the URL. For FTP, this occurs while trying to change to the remote directory. *' CURLE\_FTP\_WEIRD\_PASS\_REPLY (11)*'

After having sent the FTP password to the server, libcurl expects a proper reply. This error code indicates that an unexpected code was returned.

**CURLE\_FTP\_WEIRD\_PASV\_REPLY (13)**

libcurl failed to get a sensible result back from the server as a response to either a PASV or a EPSV command. The server is flawed.

**CURLE\_FTP\_WEIRD\_227\_FORMAT (14)**

FTP servers return a 227-line as a response to a PASV command. If libcurl fails to parse that line, this return code is passed back.

**CURLE\_FTP\_CANT\_GET\_HOST (15)**

An internal failure to lookup the host used for the new connection.

**CURLE\_FTP\_COULDNT\_SET\_TYPE (17)**

Received an error when trying to set the transfer mode to binary or ASCII.

**CURLE\_PARTIAL\_FILE (18)**

A file transfer was shorter or larger than expected. This happens when the server first reports an expected transfer size, and then delivers data that doesn't match the previously given size.

**CURLE\_FTP\_COULDNT\_RETR\_FILE (19)**

This was either a weird reply to a 'RETR' command or a zero byte transfer complete.

**CURLE\_QUOTE\_ERROR (21)**

When sending custom “QUOTE” commands to the remote server, one of the commands returned an error code that was 400 or higher (for FTP) or otherwise indicated unsuccessful completion of the command.

**CURLE\_HTTP\_RETURNED\_ERROR (22)**

This is returned if CURLOPT\_FAILONERROR is set TRUE and the HTTP server returns an error code that is &gt;= 400. (This error code was formerly known as CURLE\_HTTP\_NOT\_FOUND.)

**CURLE\_WRITE\_ERROR (23)**

An error occurred when writing received data to a local file, or an error was returned to libcurl from a write callback.

**CURLE\_UPLOAD\_FAILED (25)**

Failed starting the upload. For FTP, the server typically denied the STOR command. The error buffer usually contains the server's explanation for this. (This error code was formerly known as CURLE\_FTP\_COULDNT\_STOR\_FILE.)

**CURLE\_READ\_ERROR (26)**

There was a problem reading a local file or an error returned by the read callback.

**CURLE\_OUT\_OF\_MEMORY (27)**

A memory allocation request failed. This is serious badness and things are severely screwed up if this ever occurs.

**CURLE\_OPERATION\_TIMEDOUT (28)**

Operation timeout. The specified time-out period was reached according to the conditions.

**CURLE\_FTP\_PORT\_FAILED (30)**

The FTP PORT command returned error. This mostly happens when you haven't specified a good enough address for libcurl to use. See CURLOPT\_FTPPORT.

**CURLE\_FTP\_COULDNT\_USE\_REST (31)**

The FTP REST command returned error. This should never happen if the server is sane.

**CURLE\_RANGE\_ERROR (33)**

The server does not support or accept range requests.

**CURLE\_HTTP\_POST\_ERROR (34)**

This is an odd error that mainly occurs due to internal confusion.

**CURLE\_SSL\_CONNECT\_ERROR (35)**

A problem occurred somewhere in the SSL/TLS handshake. You really want the error buffer and read the message there as it pinpoints the problem slightly more. Could be certificates (file formats, paths, permissions), passwords, and others.

**CURLE\_FTP\_BAD\_DOWNLOAD\_RESUME (36)**

Attempting FTP resume beyond file size.

**CURLE\_FILE\_COULDNT\_READ\_FILE (37)**

A file given with <FILE://> couldn't be opened. Most likely because the file path doesn't identify an existing file. Did you check file permissions?

**CURLE\_LDAP\_CANNOT\_BIND (38)**

LDAP cannot bind. LDAP bind operation failed.

**CURLE\_LDAP\_SEARCH\_FAILED (39)**

LDAP search failed.

**CURLE\_FUNCTION\_NOT\_FOUND (41)**

Function not found. A required zlib function was not found.

**CURLE\_ABORTED\_BY\_CALLBACK (42)**

Aborted by callback. A callback returned “abort” to libcurl.

**CURLE\_BAD\_FUNCTION\_ARGUMENT (43)**

Internal error. A function was called with a bad parameter.

**CURLE\_INTERFACE\_FAILED (45)**

Interface error. A specified outgoing interface could not be used. Set which interface to use for outgoing connections' source IP address with CURLOPT\_INTERFACE. (This error code was formerly known as CURLE\_HTTP\_PORT\_FAILED.) *' CURLE\_TOO\_MANY\_REDIRECTS (47)*'

Too many redirects. When following redirects, libcurl hit the maximum amount. Set your limit with CURLOPT\_MAXREDIRS.

**CURLE\_UNKNOWN\_TELNET\_OPTION (48)**

An option set with CURLOPT\_TELNETOPTIONS was not recognized/known. Refer to the appropriate documentation.

**CURLE\_TELNET\_OPTION\_SYNTAX (49)**

A telnet option string was Illegally formatted.

**CURLE\_PEER\_FAILED\_VERIFICATION (51)**

The remote server's SSL certificate or SSH md5 fingerprint was deemed not OK.

**CURLE\_GOT\_NOTHING (52)**

Nothing was returned from the server, and under the circumstances, getting nothing is considered an error.

**CURLE\_SSL\_ENGINE\_NOTFOUND (53)**

The specified crypto engine wasn't found.

**CURLE\_SSL\_ENGINE\_SETFAILED (54)**

Failed setting the selected SSL crypto engine as default!

**CURLE\_SEND\_ERROR (55)**

Failed sending network data.

**CURLE\_RECV\_ERROR (56)**

Failure with receiving network data.

**CURLE\_SSL\_CERTPROBLEM (58)**

problem with the local client certificate.

**CURLE\_SSL\_CIPHER (59)**

Couldn't use specified cipher.

**CURLE\_SSL\_CACERT (60)**

Peer certificate cannot be authenticated with known CA certificates.

**CURLE\_BAD\_CONTENT\_ENCODING (61)**

Unrecognized transfer encoding.

**CURLE\_LDAP\_INVALID\_URL (62)**

Invalid LDAP URL.

**CURLE\_FILESIZE\_EXCEEDED (63)**

Maximum file size exceeded.

**CURLE\_USE\_SSL\_FAILED (64)**

Requested FTP SSL level failed.

**CURLE\_SEND\_FAIL\_REWIND (65)**

When doing a send operation curl had to rewind the data to retransmit, but the rewinding operation failed.

**CURLE\_SSL\_ENGINE\_INITFAILED (66)**

Initiating the SSL Engine failed.

**CURLE\_LOGIN\_DENIED (67)**

The remote server denied curl to login (Added in 7.13.1)

**CURLE\_TFTP\_NOTFOUND (68)**

File not found on TFTP server.

**CURLE\_TFTP\_PERM (69)**

Permission problem on TFTP server.

**CURLE\_REMOTE\_DISK\_FULL (70)**

Out of disk space on the server.

**CURLE\_TFTP\_ILLEGAL (71)**

Illegal TFTP operation.

**CURLE\_TFTP\_UNKNOWNID (72)**

Unknown TFTP transfer ID.

**CURLE\_REMOTE\_FILE\_EXISTS (73)**

File already exists and will not be overwritten.

**CURLE\_TFTP\_NOSUCHUSER (74)**

This error should never be returned by a properly functioning TFTP server.

**CURLE\_CONV\_FAILED (75)**

Character conversion failed.

**CURLE\_CONV\_REQD (76)**

Caller must register conversion callbacks.

**CURLE\_SSL\_CACERT\_BADFILE (77)**

Problem with reading the SSL CA cert (path? access rights?)

**CURLE\_REMOTE\_FILE\_NOT\_FOUND (78)**

The resource referenced in the URL does not exist.

**CURLE\_SSH (79)**

An unspecified error occurred during the SSH session.

**CURLE\_SSL\_SHUTDOWN\_FAILED (80)**

Failed to shut down the SSL connection.

**CURLE\_AGAIN (81)**

Socket is not ready for send/recv wait till it's ready and try again. This return code is only returned from curl\_easy\_recv(3) and curl\_easy\_send(3) (Added in 7.18.2)

**CURLE\_SSL\_CRL\_BADFILE (82)**

Failed to load CRL file (Added in 7.19.0)

**CURLE\_SSL\_ISSUER\_ERROR (83)**

Issuer check failed (Added in 7.19.0)
