# PD
[
    {
        "id": "df749ea0.1139d",
        "type": "ui_chart",
        "z": "2dc7c344.82165c",
        "name": "",
        "group": "306af8cd.b9db68",
        "order": 3,
        "width": "20",
        "height": "6",
        "label": "VibrationFFT",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "",
        "dot": false,
        "ymin": "0",
        "ymax": "200",
        "removeOlder": 1,
        "removeOlderPoints": "",
        "removeOlderUnit": "3600",
        "cutout": 0,
        "useOneColor": false,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "useOldStyle": false,
        "x": 513,
        "y": 345,
        "wires": [
            [],
            []
        ]
    },
    {
        "id": "4499c1eb.1fbe",
        "type": "function",
        "z": "2dc7c344.82165c",
        "name": "reset the chart",
        "func": "m= msg.payload;\nif(m==512){\n    msg.payload =[] \n\n    return msg;\n}\n",
        "outputs": 1,
        "noerr": 0,
        "x": 415,
        "y": 229,
        "wires": [
            [
                "df749ea0.1139d"
            ]
        ]
    },
    {
        "id": "f253072f.bbf9e8",
        "type": "counter",
        "z": "2dc7c344.82165c",
        "name": "Counter",
        "init": "0",
        "step": "1",
        "lower": "",
        "upper": "512",
        "mode": "increment",
        "outputs": 2,
        "x": 280,
        "y": 309,
        "wires": [
            [
                "4499c1eb.1fbe",
                "c1ca8e1b.afdbe"
            ],
            []
        ]
    },
    {
        "id": "c1ca8e1b.afdbe",
        "type": "function",
        "z": "2dc7c344.82165c",
        "name": "reset the counter",
        "func": "m=msg.payload;\nif (m==512){\n    msg.reset = true;\n    return msg ;\n}\n",
        "outputs": 1,
        "noerr": 0,
        "x": 274,
        "y": 404,
        "wires": [
            [
                "f253072f.bbf9e8"
            ]
        ]
    },
    {
        "id": "21c2edd5.7a9902",
        "type": "ibmiot in",
        "z": "2dc7c344.82165c",
        "authentication": "quickstart",
        "apiKey": "",
        "inputType": "evt",
        "logicalInterface": "",
        "ruleId": "",
        "deviceId": "ahmedtharwat",
        "applicationId": "",
        "deviceType": "+",
        "eventType": "+",
        "commandType": "",
        "format": "json",
        "name": "VibrationSensor",
        "service": "quickstart",
        "allDevices": "",
        "allApplications": "",
        "allDeviceTypes": true,
        "allLogicalInterfaces": "",
        "allEvents": true,
        "allCommands": "",
        "allFormats": "",
        "qos": 0,
        "x": 85,
        "y": 345,
        "wires": [
            [
                "f253072f.bbf9e8",
                "df749ea0.1139d"
            ]
        ]
    },
    {
        "id": "8ecbc33b.f0e75",
        "type": "ibmiot in",
        "z": "2dc7c344.82165c",
        "authentication": "quickstart",
        "apiKey": "",
        "inputType": "evt",
        "logicalInterface": "",
        "ruleId": "",
        "deviceId": "ahmedtharwat",
        "applicationId": "",
        "deviceType": "+",
        "eventType": "+",
        "commandType": "",
        "format": "json",
        "name": "CurrentSensor",
        "service": "quickstart",
        "allDevices": "",
        "allApplications": "",
        "allDeviceTypes": true,
        "allLogicalInterfaces": "",
        "allEvents": true,
        "allCommands": "",
        "allFormats": "",
        "qos": 0,
        "x": 94,
        "y": 551,
        "wires": [
            [
                "a2c1b337.543b1",
                "caaa2e32.053f6"
            ]
        ]
    },
    {
        "id": "a2c1b337.543b1",
        "type": "counter",
        "z": "2dc7c344.82165c",
        "name": "Counter",
        "init": "0",
        "step": "1",
        "lower": "",
        "upper": "512",
        "mode": "increment",
        "outputs": 2,
        "x": 271,
        "y": 552,
        "wires": [
            [
                "2db2be26.58b872",
                "c16917c6.addc58"
            ],
            []
        ]
    },
    {
        "id": "c16917c6.addc58",
        "type": "function",
        "z": "2dc7c344.82165c",
        "name": "Reset The Chart",
        "func": "m= msg.payload;\nif(m==512){\n    msg.payload =[] \n\n    return msg;\n}",
        "outputs": 1,
        "noerr": 0,
        "x": 431,
        "y": 513,
        "wires": [
            [
                "caaa2e32.053f6"
            ]
        ]
    },
    {
        "id": "2db2be26.58b872",
        "type": "function",
        "z": "2dc7c344.82165c",
        "name": "Reset The Counter",
        "func": "m=msg.payload;\nif (m==512){\n    msg.reset = true;\n    return msg ;\n}\n",
        "outputs": 1,
        "noerr": 0,
        "x": 274,
        "y": 618,
        "wires": [
            [
                "a2c1b337.543b1"
            ]
        ]
    },
    {
        "id": "caaa2e32.053f6",
        "type": "ui_chart",
        "z": "2dc7c344.82165c",
        "name": "",
        "group": "306af8cd.b9db68",
        "order": 4,
        "width": 0,
        "height": 0,
        "label": "CurrentFFT",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "",
        "dot": false,
        "ymin": "",
        "ymax": "",
        "removeOlder": 1,
        "removeOlderPoints": "",
        "removeOlderUnit": "3600",
        "cutout": 0,
        "useOneColor": false,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "useOldStyle": false,
        "x": 574,
        "y": 557,
        "wires": [
            [],
            []
        ]
    },
    {
        "id": "fb3fd3b8.10da6",
        "type": "ibmiot in",
        "z": "2dc7c344.82165c",
        "authentication": "quickstart",
        "apiKey": "",
        "inputType": "evt",
        "logicalInterface": "",
        "ruleId": "",
        "deviceId": "ahmedtharwat",
        "applicationId": "",
        "deviceType": "+",
        "eventType": "+",
        "commandType": "",
        "format": "json",
        "name": "Features",
        "service": "quickstart",
        "allDevices": "",
        "allApplications": "",
        "allDeviceTypes": true,
        "allLogicalInterfaces": "",
        "allEvents": true,
        "allCommands": "",
        "allFormats": "",
        "qos": 0,
        "x": 79,
        "y": 803,
        "wires": [
            [
                "462bf24c.a9a08c"
            ]
        ]
    },
    {
        "id": "8783ad2c.ca4a4",
        "type": "ui_text",
        "z": "2dc7c344.82165c",
        "group": "306af8cd.b9db68",
        "order": 1,
        "width": "5",
        "height": "3",
        "name": "",
        "label": "Motor Condition",
        "format": "{{msg.payload.values[0][8]}}",
        "layout": "row-center",
        "x": 768,
        "y": 687,
        "wires": []
    },
    {
        "id": "462bf24c.a9a08c",
        "type": "join",
        "z": "2dc7c344.82165c",
        "name": "Making array for features",
        "mode": "custom",
        "build": "array",
        "property": "payload",
        "propertyType": "msg",
        "key": "topic",
        "joiner": "\\n",
        "joinerType": "str",
        "accumulate": false,
        "timeout": "",
        "count": "4",
        "reduceRight": false,
        "reduceExp": "",
        "reduceInit": "",
        "reduceInitType": "",
        "reduceFixup": "",
        "x": 263,
        "y": 764,
        "wires": [
            [
                "35e975fd.f9f22a"
            ]
        ]
    },
    {
        "id": "35e975fd.f9f22a",
        "type": "function",
        "z": "2dc7c344.82165c",
        "name": "Features arrangement",
        "func": "m=msg.payload\nmsg.payload = {\n  \"fields\": [\n    \"SEPAL LENGTH\",\n    \"SEPAL WIDTH\",\n    \"PETAL LENGTH\",\n    \"PETAL WIDTH\"\n  ],\n  \"values\": [\n    m\n    \n  ]\n}\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 489,
        "y": 801,
        "wires": [
            [
                "79b0666b.aca768"
            ]
        ]
    },
    {
        "id": "79b0666b.aca768",
        "type": "wml",
        "z": "2dc7c344.82165c",
        "name": "RunPrediction",
        "connection": "39baac2c.a440d4",
        "wml-mode": "runPrediction",
        "model": "55e5c6c4-8f8e-4287-b64b-879bf49f4d02",
        "deployment": "835f79eb-cc36-41c5-8cbb-d5a5ab47789c",
        "modelhidden": "55e5c6c4-8f8e-4287-b64b-879bf49f4d02",
        "deploymenthidden": "",
        "x": 678,
        "y": 752,
        "wires": [
            [
                "8783ad2c.ca4a4",
                "74c8b02f.a8166",
                "a3eb77a4.6453b8"
            ]
        ]
    },
    {
        "id": "baca55ea.1c10d8",
        "type": "ui_toast",
        "z": "2dc7c344.82165c",
        "position": "dialog",
        "displayTime": "5",
        "highlight": "",
        "outputs": 1,
        "ok": "OK",
        "cancel": "",
        "topic": "There is a fault",
        "name": "",
        "x": 693,
        "y": 904,
        "wires": [
            []
        ]
    },
    {
        "id": "74c8b02f.a8166",
        "type": "function",
        "z": "2dc7c344.82165c",
        "name": "Notification",
        "func": "m=msg.payload.values[0][8];\nif (m == 'Iris-versicolor')\n{\n  return msg;\n}\n",
        "outputs": 1,
        "noerr": 0,
        "x": 762,
        "y": 829,
        "wires": [
            [
                "baca55ea.1c10d8"
            ]
        ]
    },
    {
        "id": "4ce957d3.dd6598",
        "type": "inject",
        "z": "2dc7c344.82165c",
        "name": "",
        "topic": "",
        "payload": "2.5",
        "payloadType": "num",
        "repeat": "",
        "crontab": "",
        "once": false,
        "onceDelay": 0.1,
        "x": 77,
        "y": 888,
        "wires": [
            [
                "462bf24c.a9a08c"
            ]
        ]
    },
    {
        "id": "6d7929cc.d1ec88",
        "type": "inject",
        "z": "2dc7c344.82165c",
        "name": "",
        "topic": "",
        "payload": "4.5",
        "payloadType": "num",
        "repeat": "",
        "crontab": "",
        "once": false,
        "onceDelay": 0.1,
        "x": 77,
        "y": 931,
        "wires": [
            [
                "462bf24c.a9a08c"
            ]
        ]
    },
    {
        "id": "9784b89b.49e6c8",
        "type": "inject",
        "z": "2dc7c344.82165c",
        "name": "",
        "topic": "",
        "payload": "3.9",
        "payloadType": "num",
        "repeat": "",
        "crontab": "",
        "once": false,
        "onceDelay": 0.1,
        "x": 75,
        "y": 972,
        "wires": [
            [
                "462bf24c.a9a08c"
            ]
        ]
    },
    {
        "id": "cbd22361.969d1",
        "type": "inject",
        "z": "2dc7c344.82165c",
        "name": "",
        "topic": "",
        "payload": "1.3",
        "payloadType": "num",
        "repeat": "",
        "crontab": "",
        "once": false,
        "onceDelay": 0.1,
        "x": 75,
        "y": 1012,
        "wires": [
            [
                "462bf24c.a9a08c"
            ]
        ]
    },
    {
        "id": "a3eb77a4.6453b8",
        "type": "debug",
        "z": "2dc7c344.82165c",
        "name": "",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload.values[0][8]",
        "x": 817,
        "y": 620,
        "wires": []
    },
    {
        "id": "306af8cd.b9db68",
        "type": "ui_group",
        "z": "",
        "name": "PredictiveMaintenance",
        "tab": "b5078133.3b909",
        "order": 1,
        "disp": true,
        "width": "20",
        "collapse": true
    },
    {
        "id": "39baac2c.a440d4",
        "type": "wml-config",
        "z": "",
        "host": "https://us-south.ml.cloud.ibm.com",
        "accesskey": "8e9d0931-46bd-43cc-9787-7172c1a773b6",
        "instanceid": "8e9d0931-46bd-43cc-9787-7172c1a773b6",
        "name": "MachineLearning"
    },
    {
        "id": "b5078133.3b909",
        "type": "ui_tab",
        "z": "",
        "name": "Motor 1 Analysis",
        "icon": "dashboard",
        "order": 1
    }
]

MOTOR 2 
[
    {
        "id": "7e1a18f3.fd10e8",
        "type": "ui_chart",
        "z": "9c3b0e51.acae7",
        "name": "",
        "group": "cde5b17d.d01ee",
        "order": 2,
        "width": "20",
        "height": "6",
        "label": "VibrationFFT",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "",
        "dot": false,
        "ymin": "0",
        "ymax": "200",
        "removeOlder": 1,
        "removeOlderPoints": "",
        "removeOlderUnit": "3600",
        "cutout": 0,
        "useOneColor": false,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "useOldStyle": false,
        "x": 513,
        "y": 154,
        "wires": [
            [],
            []
        ]
    },
    {
        "id": "b088cc7a.eec1",
        "type": "function",
        "z": "9c3b0e51.acae7",
        "name": "reset the chart",
        "func": "m= msg.payload;\nif(m==512){\n    msg.payload =[] \n\n    return msg;\n}\n",
        "outputs": 1,
        "noerr": 0,
        "x": 415,
        "y": 38,
        "wires": [
            [
                "7e1a18f3.fd10e8"
            ]
        ]
    },
    {
        "id": "1a5c5fff.e0b11",
        "type": "counter",
        "z": "9c3b0e51.acae7",
        "name": "Counter",
        "init": "0",
        "step": "1",
        "lower": "",
        "upper": "512",
        "mode": "increment",
        "outputs": 2,
        "x": 280,
        "y": 118,
        "wires": [
            [
                "b088cc7a.eec1",
                "dc64160.50718e8"
            ],
            []
        ]
    },
    {
        "id": "dc64160.50718e8",
        "type": "function",
        "z": "9c3b0e51.acae7",
        "name": "reset the counter",
        "func": "m=msg.payload;\nif (m==512){\n    msg.reset = true;\n    return msg ;\n}\n",
        "outputs": 1,
        "noerr": 0,
        "x": 274,
        "y": 213,
        "wires": [
            [
                "1a5c5fff.e0b11"
            ]
        ]
    },
    {
        "id": "be31babb.e84f08",
        "type": "ibmiot in",
        "z": "9c3b0e51.acae7",
        "authentication": "quickstart",
        "apiKey": "",
        "inputType": "evt",
        "logicalInterface": "",
        "ruleId": "",
        "deviceId": "ahmedtharwat",
        "applicationId": "",
        "deviceType": "+",
        "eventType": "+",
        "commandType": "",
        "format": "json",
        "name": "VibrationSensor",
        "service": "quickstart",
        "allDevices": "",
        "allApplications": "",
        "allDeviceTypes": true,
        "allLogicalInterfaces": "",
        "allEvents": true,
        "allCommands": "",
        "allFormats": "",
        "qos": 0,
        "x": 85,
        "y": 154,
        "wires": [
            [
                "1a5c5fff.e0b11",
                "7e1a18f3.fd10e8"
            ]
        ]
    },
    {
        "id": "5d9a91a5.d63aa",
        "type": "ibmiot in",
        "z": "9c3b0e51.acae7",
        "authentication": "quickstart",
        "apiKey": "",
        "inputType": "evt",
        "logicalInterface": "",
        "ruleId": "",
        "deviceId": "ahmedtharwat",
        "applicationId": "",
        "deviceType": "+",
        "eventType": "+",
        "commandType": "",
        "format": "json",
        "name": "CurrentSensor",
        "service": "quickstart",
        "allDevices": "",
        "allApplications": "",
        "allDeviceTypes": true,
        "allLogicalInterfaces": "",
        "allEvents": true,
        "allCommands": "",
        "allFormats": "",
        "qos": 0,
        "x": 94,
        "y": 360,
        "wires": [
            [
                "4c3506a0.490238",
                "8d512eb2.5f288"
            ]
        ]
    },
    {
        "id": "4c3506a0.490238",
        "type": "counter",
        "z": "9c3b0e51.acae7",
        "name": "Counter",
        "init": "0",
        "step": "1",
        "lower": "",
        "upper": "512",
        "mode": "increment",
        "outputs": 2,
        "x": 271,
        "y": 361,
        "wires": [
            [
                "195cac7a.0d9344",
                "22ad8160.db18ce"
            ],
            []
        ]
    },
    {
        "id": "22ad8160.db18ce",
        "type": "function",
        "z": "9c3b0e51.acae7",
        "name": "Reset The Chart",
        "func": "m= msg.payload;\nif(m==512){\n    msg.payload =[] \n\n    return msg;\n}",
        "outputs": 1,
        "noerr": 0,
        "x": 431,
        "y": 322,
        "wires": [
            [
                "8d512eb2.5f288"
            ]
        ]
    },
    {
        "id": "195cac7a.0d9344",
        "type": "function",
        "z": "9c3b0e51.acae7",
        "name": "Reset The Counter",
        "func": "m=msg.payload;\nif (m==512){\n    msg.reset = true;\n    return msg ;\n}\n",
        "outputs": 1,
        "noerr": 0,
        "x": 274,
        "y": 427,
        "wires": [
            [
                "4c3506a0.490238"
            ]
        ]
    },
    {
        "id": "8d512eb2.5f288",
        "type": "ui_chart",
        "z": "9c3b0e51.acae7",
        "name": "",
        "group": "cde5b17d.d01ee",
        "order": 3,
        "width": "20",
        "height": "6",
        "label": "CurrentFFT",
        "chartType": "line",
        "legend": "false",
        "xformat": "HH:mm:ss",
        "interpolate": "linear",
        "nodata": "",
        "dot": false,
        "ymin": "",
        "ymax": "",
        "removeOlder": 1,
        "removeOlderPoints": "",
        "removeOlderUnit": "3600",
        "cutout": 0,
        "useOneColor": false,
        "colors": [
            "#1f77b4",
            "#aec7e8",
            "#ff7f0e",
            "#2ca02c",
            "#98df8a",
            "#d62728",
            "#ff9896",
            "#9467bd",
            "#c5b0d5"
        ],
        "useOldStyle": false,
        "x": 574,
        "y": 366,
        "wires": [
            [],
            []
        ]
    },
    {
        "id": "eccfcd46.7354d",
        "type": "ibmiot in",
        "z": "9c3b0e51.acae7",
        "authentication": "quickstart",
        "apiKey": "",
        "inputType": "evt",
        "logicalInterface": "",
        "ruleId": "",
        "deviceId": "ahmedtharwat",
        "applicationId": "",
        "deviceType": "+",
        "eventType": "+",
        "commandType": "",
        "format": "json",
        "name": "Features",
        "service": "quickstart",
        "allDevices": "",
        "allApplications": "",
        "allDeviceTypes": true,
        "allLogicalInterfaces": "",
        "allEvents": true,
        "allCommands": "",
        "allFormats": "",
        "qos": 0,
        "x": 79,
        "y": 612,
        "wires": [
            [
                "361c328c.fe742e"
            ]
        ]
    },
    {
        "id": "6fa5b81a.0e9508",
        "type": "ui_text",
        "z": "9c3b0e51.acae7",
        "group": "cde5b17d.d01ee",
        "order": 1,
        "width": "5",
        "height": "3",
        "name": "",
        "label": "Motor Condition",
        "format": "{{msg.payload.values[0][8]}}",
        "layout": "row-center",
        "x": 768,
        "y": 496,
        "wires": []
    },
    {
        "id": "361c328c.fe742e",
        "type": "join",
        "z": "9c3b0e51.acae7",
        "name": "Making array for features",
        "mode": "custom",
        "build": "array",
        "property": "payload",
        "propertyType": "msg",
        "key": "topic",
        "joiner": "\\n",
        "joinerType": "str",
        "accumulate": false,
        "timeout": "",
        "count": "4",
        "reduceRight": false,
        "reduceExp": "",
        "reduceInit": "",
        "reduceInitType": "",
        "reduceFixup": "",
        "x": 263,
        "y": 573,
        "wires": [
            [
                "8272377a.53d538"
            ]
        ]
    },
    {
        "id": "8272377a.53d538",
        "type": "function",
        "z": "9c3b0e51.acae7",
        "name": "Features arrangement",
        "func": "m=msg.payload\nmsg.payload = {\n  \"fields\": [\n    \"SEPAL LENGTH\",\n    \"SEPAL WIDTH\",\n    \"PETAL LENGTH\",\n    \"PETAL WIDTH\"\n  ],\n  \"values\": [\n    m\n    \n  ]\n}\nreturn msg;",
        "outputs": 1,
        "noerr": 0,
        "x": 489,
        "y": 610,
        "wires": [
            [
                "c5c64aec.7b2ce8"
            ]
        ]
    },
    {
        "id": "c5c64aec.7b2ce8",
        "type": "wml",
        "z": "9c3b0e51.acae7",
        "name": "RunPrediction",
        "connection": "39baac2c.a440d4",
        "wml-mode": "runPrediction",
        "model": "55e5c6c4-8f8e-4287-b64b-879bf49f4d02",
        "deployment": "835f79eb-cc36-41c5-8cbb-d5a5ab47789c",
        "modelhidden": "55e5c6c4-8f8e-4287-b64b-879bf49f4d02",
        "deploymenthidden": "",
        "x": 678,
        "y": 561,
        "wires": [
            [
                "6fa5b81a.0e9508",
                "defd4ad9.b0fd08",
                "5911f9e2.f90258"
            ]
        ]
    },
    {
        "id": "501c4e28.e9007",
        "type": "ui_toast",
        "z": "9c3b0e51.acae7",
        "position": "dialog",
        "displayTime": "5",
        "highlight": "",
        "outputs": 1,
        "ok": "OK",
        "cancel": "",
        "topic": "There is a fault",
        "name": "",
        "x": 693,
        "y": 713,
        "wires": [
            []
        ]
    },
    {
        "id": "defd4ad9.b0fd08",
        "type": "function",
        "z": "9c3b0e51.acae7",
        "name": "Notification",
        "func": "m=msg.payload.values[0][8];\nif (m == 'Iris-versicolor')\n{\n  return msg;\n}\n",
        "outputs": 1,
        "noerr": 0,
        "x": 762,
        "y": 638,
        "wires": [
            [
                "501c4e28.e9007"
            ]
        ]
    },
    {
        "id": "49643997.57d8d8",
        "type": "inject",
        "z": "9c3b0e51.acae7",
        "name": "",
        "topic": "",
        "payload": "2.5",
        "payloadType": "num",
        "repeat": "",
        "crontab": "",
        "once": false,
        "onceDelay": 0.1,
        "x": 77,
        "y": 697,
        "wires": [
            [
                "361c328c.fe742e"
            ]
        ]
    },
    {
        "id": "5ca787e7.e48418",
        "type": "inject",
        "z": "9c3b0e51.acae7",
        "name": "",
        "topic": "",
        "payload": "4.5",
        "payloadType": "num",
        "repeat": "",
        "crontab": "",
        "once": false,
        "onceDelay": 0.1,
        "x": 77,
        "y": 740,
        "wires": [
            [
                "361c328c.fe742e"
            ]
        ]
    },
    {
        "id": "e76720b7.45b61",
        "type": "inject",
        "z": "9c3b0e51.acae7",
        "name": "",
        "topic": "",
        "payload": "3.9",
        "payloadType": "num",
        "repeat": "",
        "crontab": "",
        "once": false,
        "onceDelay": 0.1,
        "x": 75,
        "y": 781,
        "wires": [
            [
                "361c328c.fe742e"
            ]
        ]
    },
    {
        "id": "4c93b688.87b278",
        "type": "inject",
        "z": "9c3b0e51.acae7",
        "name": "",
        "topic": "",
        "payload": "1.3",
        "payloadType": "num",
        "repeat": "",
        "crontab": "",
        "once": false,
        "onceDelay": 0.1,
        "x": 75,
        "y": 821,
        "wires": [
            [
                "361c328c.fe742e"
            ]
        ]
    },
    {
        "id": "5911f9e2.f90258",
        "type": "debug",
        "z": "9c3b0e51.acae7",
        "name": "",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload.values[0][8]",
        "x": 817,
        "y": 429,
        "wires": []
    },
    {
        "id": "cde5b17d.d01ee",
        "type": "ui_group",
        "z": "",
        "name": "PredictiveMaintenance",
        "tab": "7fb35521.7f87cc",
        "order": 1,
        "disp": true,
        "width": "20",
        "collapse": true
    },
    {
        "id": "39baac2c.a440d4",
        "type": "wml-config",
        "z": "",
        "host": "https://us-south.ml.cloud.ibm.com",
        "accesskey": "8e9d0931-46bd-43cc-9787-7172c1a773b6",
        "instanceid": "8e9d0931-46bd-43cc-9787-7172c1a773b6",
        "name": "MachineLearning"
    },
    {
        "id": "7fb35521.7f87cc",
        "type": "ui_tab",
        "z": "",
        "name": "Motor 2 Analysis",
        "icon": "dashboard",
        "order": 2
    }
]
