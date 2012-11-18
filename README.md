Paypal_ec : Paypal Express Checkout Library for CodeIgniter
===========================================================

This is a simple implementation of the Paypal Express Checkout. It's not thorough as it only handles the Sale action type. But for most people, this is all that you need. This library does not handle Order and Authorization (yet - no promises). It also does NOT handle recurring payments too.

How to use
----------

- this library requires PHP cURL library
- put Paypal_ec.php in your application/library folder
- you can load Paypal_ec from any controller functions but I suggest the __construct()
- you need to create a credential array before loading the library.

`
	  $paypal_credentials = array(
			'API_username' => 'paypal_api1.e-sentral.com',
			'API_signature' => 'AEmMdYb3RRE122AFNn0TfbAxyhYuA.5J3wHV4AfizBZMLpQsQ1Ybaz-e',
			'API_password' => '37SCHA3TYBJFQ43T',
			'sandbox_status' => true
	  );	  
	  
	  $this->load->library('paypal_ec', $paypal_credentials);
`

- test.php is your sample controller, with some notes and documentations in between. make sure you read through them.

About Paypal Express Checkout
-----------------------------

If you don't yet understand how Paypal Express Checkout works, make sure you read through Paypal's documentation about it. https://cms.paypal.com/en/cgi-bin/?cmd=_render-content&content_ID=developer/e_howto_api_ECGettingStarted

But basically, Paypal Express Checkout has three main API calls. SetExpressCheckout, GetExpressCheckoutDetails and DoExpressCheckoutPayment

- *SetExpressCheckout* - calling this API sets the stage for the next following steps. You send payment information and Paypal will return with a token string that you use to redirect customers to Paypal
- *GetExpressCheckoutDetails* - After completing the process at Paypal, Paypal will redirect customers to your return_url you set during SetExpressCheckout. At your return_url, you should call GetExpressCheckoutDetails to get the details of the transactions.
- *DoExpressCheckoutPayment* - After getting the transaction details, you can call DoExpressCheckoutPayment to complete the transaction and collect your money.

