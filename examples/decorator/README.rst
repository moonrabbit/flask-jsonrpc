decorator
=========

The basic method decorated dealing any extra parameter and do some thing.


Testing your service
********************

1. Running

::

    $ python decorator.py
     * Running on http://0.0.0.0:5000/


2. Testing

::

    $ curl -i -X POST  -H "Content-Type: application/json" -d '{"jsonrpc": "2.0", "method": "App.index", "params": {}, "id": "1", "terminal_id":  1}' http://localhost:5000/api
    HTTP/1.0 200 OK
    Content-Type: application/json
    Content-Length: 67
    Server: Werkzeug/0.8.3 Python/2.7.7
    Date: Mon, 07 Jul 2014 12:31:50 GMT

    {
      "id": "1",
      "jsonrpc": "2.0",
      "result": "Terminal ID: 1"
    }


::

    $ curl -i -X POST  -H "Content-Type: application/json" -d '{"jsonrpc": "2.0", "method": "App.index", "params": {}, "id": "1", "terminal_id":  0}' http://localhost:5000/api
    HTTP/1.0 200 OK
    Content-Type: application/json
    Content-Length: 750
    Server: Werkzeug/0.8.3 Python/2.7.7
    Date: Mon, 07 Jul 2014 12:36:48 GMT

    {
      "error": {
        "code": 500,
        "data": null,
        "executable": "/usr/bin/python2",
        "message": "OtherError: Invalid terminal ID",
        "name": "OtherError",
        "stack": "Traceback (most recent call last):\n  File \"/home/nycholas/project/src/o_lalertom/flask/flask-jsonrpc/examples/../flask_jsonrpc/site.py\", line 208, in response_dict\n    R = apply_version[version](method, D['params'])\n  File \"/home/nycholas/project/src/o_lalertom/flask/flask-jsonrpc/examples/../flask_jsonrpc/site.py\", line 168, in <lambda>\n    '2.0': lambda f, p: f(**encode_kw(p)) if type(p) is dict else f(*p),\n  File \"decorator.py\", line 53, in wrapped\n    raise OtherError('Invalid terminal ID')\nOtherError\n"
      },
      "id": "1",
      "jsonrpc": "2.0"
    }
