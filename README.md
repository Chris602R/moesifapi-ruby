MoesifApi Lib for Ruby
======================

[Source Code on GitHub](https://github.com/moesif/moesifapi-ruby)

__Check out Moesif's
[Ruby developer documentation](https://www.moesif.com/developer-documentation) to learn more__

(Documentation access requires an active account)

How to configure:
=================
The generated code might need to be configured with your API credentials. To do that,
open the file "configuration.rb" and edit it's contents.

Alternatively, you can modify the Configuration parameters at run-time through the following:
```
MoesifApi::Configuration.your_paramater = YOUR_VALUE
```
Install from RubyGems
=====================
gem install moesif_api

How to build and install manually:
==================================
The generated code depends on a few Ruby gems. The references to these gems are
added in the gemspec file. The easiest way to resolve the dependencies,
build the gem and install it is through Rake:

  1. Install Rake if not already installed: `gem install rake`
  2. Install Bundler if not already installed: `gem install bundler`
  3. From terminal/cmd navigate to the root directory of the SDK.
  4. Invoke: `rake install`

Alternatively, you can build and install the gem manually:

  1. From terminal/cmd navigate to the root directory of the SDK.
  2. Run the build command: `gem build moesif_api.gemspec`
  3. Run the install command: `gem install ./moesif_api-1.0.0.gem`

Note: You will need to have internet access for this step.

How  to test:
=============
You can test the generated SDK and the server with automatically generated test
cases as follows:

  1. From terminal/cmd navigate to the root directory of the SDK.
  2. Invoke: `bundle exec rake`

How to use:
===========
After having installed the gem, you can easily use the SDK following these steps.

  1. Create a "moesif_api_test.rb" file in the root directory.
  2. Use any controller as follows:
```ruby
require 'moesif_api'

api_client = MoesifApi::MoesifAPIClient.new(my_application_id)
api_controller = api_client.api_controller

req_headers = JSON.parse('{'\
  '"Host": "api.acmeinc.com",'\
  '"Accept": "*/*",'\
  '"Connection": "Keep-Alive",'\
  '"User-Agent": "Dalvik/2.1.0 (Linux; U; Android 5.0.2; C6906 Build/14.5.A.0.242)",'\
  '"Content-Type": "application/json",'\
  '"Content-Length": "126",'\
  '"Accept-Encoding": "gzip"'\
'}')

req_body = JSON.parse( '{'\
  '"items": ['\
    '{'\
      '"type": 1,'\
      '"id": "fwfrf"'\
    '},'\
    '{'\
      '"type": 2,'\
      '"id": "d43d3f"'\
    '}'\
  ']'\
'}')

rsp_headers = JSON.parse('{'\
  '"Date": "Tue, 23 Aug 2016 23:46:49 GMT",'\
                '"Vary": "Accept-Encoding",'\
  '"Pragma": "no-cache",'\
  '"Expires": "-1",'\
  '"Content-Type": "application/json; charset=utf-8",'\
                '"Cache-Control": "no-cache"'\
'}')

rsp_body = JSON.parse('{'\
  '"Error": "InvalidArgumentException",'\
  '"Message": "Missing field field_a"'\
'}')


event_req = EventRequestModel.new()
event_req.time = "2016-09-09T04:45:42.914"
event_req.uri = "https://api.acmeinc.com/items/reviews/"
event_req.verb = "PATCH"
event_req.api_version = "1.1.0"
event_req.ip_address = "61.48.220.123"
event_req.headers = req_headers
event_req.body = req_body

event_rsp = EventResponseModel.new()
event_rsp.time = "2016-09-09T04:45:42.914"
event_rsp.status = 500
event_rsp.headers = rsp_headers
event_rsp.body = rsp_body

event_model = EventModel.new()
event_model.request = event_req
event_model.response = event_rsp
event_model.user_id ="my_user_id"
event_model.session_token = "23jdf0owekfmcn4u3qypxg09w4d8ayrcdx8nu2ng]s98y18cx98q3yhwmnhcfx43f"

# Perform the API call through the SDK function
response = api_controller.create_event(event_model)
```
