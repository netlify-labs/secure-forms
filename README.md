<h1> Secure Forms with VGS
<a href="https://app.netlify.com/start/deploy?repository=https://github.com/netlify-labs/secure-forms">
  <img align="right" src="https://camo.githubusercontent.com/be2eb66bb727e25655f1dcff88c2fdca82a77513/68747470733a2f2f7777772e6e65746c6966792e636f6d2f696d672f6465706c6f792f627574746f6e2e737667" class="deploy-button" alt="deploy to netlify">
</a>
</h1>

Example of how to use Very Good Security Netlify add-on

## Use cases

Using the vgs add-on you can collect and protect sensitive data.

**Here are some use cases:**

- Collect credit card data in a PCI compliant manner
- Protect personally identifiable information (PII) and healthcare data
- Store billing details securely
- Redact function logs

## Video

<a href="https://www.youtube.com/watch?v=k2I_4u8_I9s"><img width="600" src="https://user-images.githubusercontent.com/532272/58996669-1baea380-87ae-11e9-826d-c0fdfd839d07.jpg" /></a>

## How it works

<a href="https://youtu.be/wtYzLdpSeJo"><img width="600" src="https://user-images.githubusercontent.com/532272/58996723-51538c80-87ae-11e9-8333-a659cf23caa6.jpg" /></a>

## Setup

1. **Create and Deploy a new Netlify site**

    You can use an [this repo](https://app.netlify.com/start/deploy?repository=https://github.com/netlify-labs/secure-forms)

2. **[Add a form to your site](https://www.netlify.com/docs/form-handling/)**

		Include the `netlify` attribute so Netlify picks up the submissions

		```html
		<form name="my-form" method="POST" netlify>
		  <p>
		    <label>Your Name: <input type="text" name="name" /></label>
		  </p>
		  <p>
		    <label>Your Email: <input type="email" name="email" /></label>
		  </p>
		  <p>
		    <label>SSN: <input type="text" name="ssn" /></label>
		  </p>
		  <p>
		    <label>Message: <textarea name="message"></textarea></label>
		  </p>
		  <p>
		    <button type="submit">Send Info</button>
		  </p>
		</form>
		```

3. **After creating your form, add the secure fields**

		```
		<form name="my-form" method="POST" netlify secure>
			<p>
			  <label>Your Name: <input type="text" name="name" /></label>
			</p>
			<p>
			  <label>Your Email: <input type="email" name="email" /></label>
			</p>
			<p>
			  <label>SSN: <input type="text" name="ssn" data-secure-field /></label>
			</p>
			<p>
			  <label>Message: <textarea name="message"></textarea></label>
			</p>
			<p>
			  <button type="submit">Send Info</button>
			</p>
		</form>
		```

4. **Install the `vgs` add-on**

    Using the [`netlify-cli`](http://cli.netlify.com) add the `add-on` to your site.

    ```
    netlify addons:create vgs
    ```

    Then auth with `vgs`

    ```
    netlify addons:auths vgs
    ```

5. **Then tell VGS the path to your secure form**


    ```
    netlify addons:config vgs --path /
    ```

6. **Visit your site and submit your form.**


		View the form submission in the Netlify UI to verify the form redaction is working.