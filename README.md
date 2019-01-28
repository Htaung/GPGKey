
<h1>How to Use GPG Keys to Send Encrypted Messages</h1>

<h2>Ref : https://www.linode.com/docs/security/encryption/gpg-keys-to-send-encrypted-messages/#decrypt-a-message </h2>

Delete public key 
<code>
<pre>
gpg --delete-key aung@gmail.com 
</code>
</pre>

Delte private key 
<code>
<pre>
gpg --delete-secret-key aung@gmail.com 
</pre>
</code>

List key
<code>
<pre>
gpg --list-keys
</pre>
</code>
 

<h2>1.Create gpg key in My computer(in windows)  // My Web Sever </h2>
<p>
RealName ==> aung email==> aung@gmail.com
<code>
<pre>
gpg --full-generate-key 
</code>
</pre>
</p> 


<h2>Create gpg key in My girl friend computer (in Ubuntu) // Api Server like banking </h2>
<p>
RealName ==> thiri email==> thiri@gmail.com
<code>
<pre>
gpg --gen-key 
</code>
</pre>
</p> 


<h2>2.Export public key in aung Computer <h2>
<p>
<code>
<pre>
gpg --armor --output aung_public-key.asc --export aung@gmail.com 
</code>
</pre>
</p>

 
<p>
<h2>Export public key in My girl friend Computer </h2>
<code>
<pre>
gpg --armor --output thiri_EN_PUBLIC.asc--export thiri@gmail.com 
</code>
</pre>
</p>

 

<h2>3.Import public key and sign </h2>
<p>
In DBS PayLah Computer 
<code>
<pre>
gpg --sign-key aung@gmail.com 
</code>
</pre>
<p>
 

<h2>In aung Computer </h2>
<p>
<code>
<pre>
gpg --sign-key thiri@gmail.com 
</code>
</pre>
</p>
 
<h2>4.Encrypt request msg from aung Computer </h2>
<p>
<code>
<pre>
gpg --output webcheckout_req.txt.gpg --encrypt --sign --armor --compress-algo zip -r thiri@gmail.com webcheckout_req.txt 
</code>
</pre>
</p>
 

 



<h2>Decrpt request  msg from My girl friend Computer </h2>
<p>
<code>
<pre>
gpg --output decryptMsg --decrypt webcheckout_req.txt.gpg 
</code>
</pre>
</p>

 

<h2>Encrypt response msg from My girl friend Computer </h2>
<p>
<code>
<pre>
gpg --output webcheckout_res.txt.gpg --encrypt --sign --armor --compress-algo zip -r aung@gmail.com webcheckout_res.txt 
</code>
</pre>
</p>

 
<h2>Decrpt request  msg from My girl friend Computer</h2>
<p>
<code>
<pre>
gpg --output decryptMsg --decrypt webcheckout_res.txt.gpg
</code>
</pre>
</p>
