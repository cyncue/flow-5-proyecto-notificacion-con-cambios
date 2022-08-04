# flow-5
Este repositorio contiene las alarmas cuando hay cambios de temperatura en el contenedor

[
    {
        "id": "aea0ddd0260a1dd6",
        "type": "tab",
        "label": "Flow 5",
        "disabled": false,
        "info": "",
        "env": []
    },
    {
        "id": "6c19f3d51ee01d7d",
        "type": "mqtt in",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "topic": "capstone/team15/command",
        "qos": "2",
        "datatype": "auto-detect",
        "broker": "ecd64a3cd51ca71d",
        "nl": false,
        "rap": true,
        "rh": 0,
        "inputs": 0,
        "x": 200,
        "y": 80,
        "wires": [
            [
                "ce28f82839677cb5",
                "ac619b0493d5ff26",
                "397d972310ba2d1d"
            ]
        ]
    },
    {
        "id": "397d972310ba2d1d",
        "type": "switch",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "property": "payload",
        "propertyType": "msg",
        "rules": [
            {
                "t": "gt",
                "v": "MAX",
                "vt": "flow"
            },
            {
                "t": "lt",
                "v": "MIN",
                "vt": "flow"
            },
            {
                "t": "else"
            }
        ],
        "checkall": "true",
        "repair": false,
        "outputs": 3,
        "x": 170,
        "y": 160,
        "wires": [
            [
                "b6a8e82ba06a31e7"
            ],
            [
                "5cc8d19792802e4f"
            ],
            [
                "a5567e58bd867819"
            ]
        ]
    },
    {
        "id": "b6a8e82ba06a31e7",
        "type": "change",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "la temperatura del contenedor es muy alta",
                "tot": "str"
            },
            {
                "t": "set",
                "p": "icon",
                "pt": "msg",
                "to": "<i class=\"fa fa-exclamation-triangle\" aria-hidden=\"true\"></i>",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 340,
        "y": 140,
        "wires": [
            [
                "3b7b2c5f21398524"
            ]
        ]
    },
    {
        "id": "5cc8d19792802e4f",
        "type": "change",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "la temoeratura del contenedor es muy baja",
                "tot": "str"
            },
            {
                "t": "set",
                "p": "icon",
                "pt": "msg",
                "to": "<i class=\"fa fa-exclamation-circle\" aria-hidden=\"true\"></i>",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 340,
        "y": 180,
        "wires": [
            [
                "3b7b2c5f21398524"
            ]
        ]
    },
    {
        "id": "a5567e58bd867819",
        "type": "change",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "todo ok",
                "tot": "str"
            },
            {
                "t": "set",
                "p": "icon",
                "pt": "msg",
                "to": "<i class=\"fa fa-lightbulb-o\" aria-hidden=\"true\"></i>",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 340,
        "y": 220,
        "wires": [
            [
                "3b7b2c5f21398524"
            ]
        ]
    },
    {
        "id": "3b7b2c5f21398524",
        "type": "rbe",
        "z": "aea0ddd0260a1dd6",
        "name": "rbe",
        "func": "rbe",
        "gap": "",
        "start": "",
        "inout": "out",
        "septopics": false,
        "property": "payload",
        "topi": "topic",
        "x": 510,
        "y": 180,
        "wires": [
            [
                "a5f14428b5609310",
                "be83981a4a2cf729",
                "071ffe3ddc707a28",
                "78e8a8912e86a52d"
            ]
        ]
    },
    {
        "id": "071ffe3ddc707a28",
        "type": "e-mail",
        "z": "aea0ddd0260a1dd6",
        "server": "smtp.gmail.com",
        "port": "465",
        "secure": true,
        "tls": true,
        "name": "cynthia.cuellar@uppuebla.edu.mx",
        "dname": "",
        "x": 780,
        "y": 320,
        "wires": []
    },
    {
        "id": "a5f14428b5609310",
        "type": "ui_text",
        "z": "aea0ddd0260a1dd6",
        "group": "86e1f10557cab5ed",
        "order": 1,
        "width": 0,
        "height": 0,
        "name": "",
        "label": "contenedor",
        "format": "{{msg.payload}}",
        "layout": "row-spread",
        "className": "",
        "x": 690,
        "y": 220,
        "wires": []
    },
    {
        "id": "ac619b0493d5ff26",
        "type": "ui_gauge",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "group": "86e1f10557cab5ed",
        "order": 0,
        "width": 0,
        "height": 0,
        "gtype": "gage",
        "title": "gauge",
        "label": "units",
        "format": "{{value}}",
        "min": 0,
        "max": "35",
        "colors": [
            "#00b500",
            "#e6e600",
            "#ca3838"
        ],
        "seg1": "",
        "seg2": "",
        "className": "",
        "x": 650,
        "y": 120,
        "wires": []
    },
    {
        "id": "ce28f82839677cb5",
        "type": "debug",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 630,
        "y": 60,
        "wires": []
    },
    {
        "id": "be83981a4a2cf729",
        "type": "debug",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 690,
        "y": 260,
        "wires": []
    },
    {
        "id": "c8b32f05f81edace",
        "type": "ui_slider",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "label": "MAX",
        "tooltip": "",
        "group": "641042f35d4db302",
        "order": 6,
        "width": 0,
        "height": 0,
        "passthru": true,
        "outs": "end",
        "topic": "topic",
        "topicType": "msg",
        "min": 0,
        "max": "35",
        "step": 1,
        "className": "",
        "x": 150,
        "y": 400,
        "wires": [
            [
                "270dc13e7ec4b3fc"
            ]
        ]
    },
    {
        "id": "d0d8947ffb5615af",
        "type": "ui_slider",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "label": "MIN",
        "tooltip": "",
        "group": "641042f35d4db302",
        "order": 7,
        "width": 0,
        "height": 0,
        "passthru": true,
        "outs": "end",
        "topic": "topic",
        "topicType": "msg",
        "min": 0,
        "max": "35",
        "step": 1,
        "className": "",
        "x": 150,
        "y": 500,
        "wires": [
            [
                "b20e36220903d9a4"
            ]
        ]
    },
    {
        "id": "972c7c7280261188",
        "type": "change",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "MAX",
                "pt": "flow",
                "to": "payload",
                "tot": "msg",
                "dc": true
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 510,
        "y": 440,
        "wires": [
            [
                "b39d45ed07b2be34"
            ]
        ]
    },
    {
        "id": "158c964dcfd19af5",
        "type": "change",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "MIN",
                "pt": "flow",
                "to": "payload",
                "tot": "msg",
                "dc": true
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 510,
        "y": 480,
        "wires": [
            [
                "b39d45ed07b2be34"
            ]
        ]
    },
    {
        "id": "78e8a8912e86a52d",
        "type": "ui_text",
        "z": "aea0ddd0260a1dd6",
        "group": "79c7e6c65e0d3803",
        "order": 6,
        "width": 0,
        "height": 0,
        "name": "",
        "label": "Icono",
        "format": "{{msg.icon}}",
        "layout": "row-spread",
        "className": "",
        "x": 710,
        "y": 180,
        "wires": []
    },
    {
        "id": "0d81749fcd31230f",
        "type": "link in",
        "z": "aea0ddd0260a1dd6",
        "name": "link in 1",
        "links": [
            "e4cf7bfef1d29185"
        ],
        "x": 65,
        "y": 400,
        "wires": [
            [
                "c8b32f05f81edace"
            ]
        ]
    },
    {
        "id": "559641f6dc183291",
        "type": "link in",
        "z": "aea0ddd0260a1dd6",
        "name": "link in 2",
        "links": [],
        "x": 55,
        "y": 500,
        "wires": [
            [
                "d0d8947ffb5615af"
            ]
        ]
    },
    {
        "id": "40ae1dfba5502d57",
        "type": "change",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "MAX",
                "tot": "flow"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 520,
        "y": 360,
        "wires": [
            [
                "e4cf7bfef1d29185"
            ]
        ]
    },
    {
        "id": "08a3eff2de98ef48",
        "type": "change",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "El valor MAX debe ser mayor que MIN",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 520,
        "y": 400,
        "wires": [
            [
                "30837f5ef291b7e8"
            ]
        ]
    },
    {
        "id": "b563b3de6a2d391e",
        "type": "change",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "El valor MIN debe ser menor que MAX",
                "tot": "str"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 520,
        "y": 520,
        "wires": [
            [
                "a0dd1a258a610443"
            ]
        ]
    },
    {
        "id": "3f382239043c9d9a",
        "type": "change",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "rules": [
            {
                "t": "set",
                "p": "payload",
                "pt": "msg",
                "to": "MIN",
                "tot": "flow"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 520,
        "y": 560,
        "wires": [
            [
                "f0ec0a85c2815bef"
            ]
        ]
    },
    {
        "id": "270dc13e7ec4b3fc",
        "type": "switch",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "property": "payload",
        "propertyType": "msg",
        "rules": [
            {
                "t": "lte",
                "v": "MIN",
                "vt": "flow"
            },
            {
                "t": "else"
            }
        ],
        "checkall": "true",
        "repair": false,
        "outputs": 2,
        "x": 290,
        "y": 400,
        "wires": [
            [
                "40ae1dfba5502d57",
                "08a3eff2de98ef48"
            ],
            [
                "972c7c7280261188"
            ]
        ]
    },
    {
        "id": "b20e36220903d9a4",
        "type": "switch",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "property": "payload",
        "propertyType": "msg",
        "rules": [
            {
                "t": "lte",
                "v": "MAX",
                "vt": "flow"
            },
            {
                "t": "else"
            }
        ],
        "checkall": "true",
        "repair": false,
        "outputs": 2,
        "x": 290,
        "y": 500,
        "wires": [
            [
                "b563b3de6a2d391e",
                "3f382239043c9d9a"
            ],
            [
                "158c964dcfd19af5"
            ]
        ]
    },
    {
        "id": "e4cf7bfef1d29185",
        "type": "link out",
        "z": "aea0ddd0260a1dd6",
        "name": "link out 1",
        "mode": "link",
        "links": [
            "0d81749fcd31230f"
        ],
        "x": 645,
        "y": 360,
        "wires": []
    },
    {
        "id": "b39d45ed07b2be34",
        "type": "change",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "rules": [
            {
                "t": "delete",
                "p": "payload",
                "pt": "msg"
            },
            {
                "t": "set",
                "p": "ui_control.seg1",
                "pt": "msg",
                "to": "MIN",
                "tot": "flow"
            },
            {
                "t": "set",
                "p": "ui_control.seg2",
                "pt": "msg",
                "to": "MAX",
                "tot": "flow"
            }
        ],
        "action": "",
        "property": "",
        "from": "",
        "to": "",
        "reg": false,
        "x": 700,
        "y": 460,
        "wires": [
            [
                "771aa020284978eb",
                "ac619b0493d5ff26"
            ]
        ]
    },
    {
        "id": "f0ec0a85c2815bef",
        "type": "link out",
        "z": "aea0ddd0260a1dd6",
        "name": "link out 2",
        "mode": "link",
        "links": [],
        "x": 655,
        "y": 560,
        "wires": []
    },
    {
        "id": "30837f5ef291b7e8",
        "type": "ui_toast",
        "z": "aea0ddd0260a1dd6",
        "position": "dialog",
        "displayTime": "3",
        "highlight": "",
        "sendall": true,
        "outputs": 1,
        "ok": "OK",
        "cancel": "Cancel",
        "raw": false,
        "className": "",
        "topic": "",
        "name": "",
        "x": 730,
        "y": 400,
        "wires": [
            []
        ]
    },
    {
        "id": "a0dd1a258a610443",
        "type": "ui_toast",
        "z": "aea0ddd0260a1dd6",
        "position": "dialog",
        "displayTime": "3",
        "highlight": "",
        "sendall": true,
        "outputs": 1,
        "ok": "OK",
        "cancel": "Cancel",
        "raw": false,
        "className": "",
        "topic": "",
        "name": "",
        "x": 710,
        "y": 520,
        "wires": [
            []
        ]
    },
    {
        "id": "771aa020284978eb",
        "type": "debug",
        "z": "aea0ddd0260a1dd6",
        "name": "",
        "active": true,
        "tosidebar": true,
        "console": false,
        "tostatus": false,
        "complete": "payload",
        "targetType": "msg",
        "statusVal": "",
        "statusType": "auto",
        "x": 910,
        "y": 460,
        "wires": []
    },
    {
        "id": "ecd64a3cd51ca71d",
        "type": "mqtt-broker",
        "name": "HIVEMQ",
        "broker": "broker.hivemq.com",
        "port": "1883",
        "clientid": "",
        "autoConnect": true,
        "usetls": false,
        "protocolVersion": "4",
        "keepalive": "60",
        "cleansession": true,
        "birthTopic": "",
        "birthQos": "0",
        "birthPayload": "",
        "birthMsg": {},
        "closeTopic": "",
        "closeQos": "0",
        "closePayload": "",
        "closeMsg": {},
        "willTopic": "",
        "willQos": "0",
        "willPayload": "",
        "willMsg": {},
        "userProps": "",
        "sessionExpiry": ""
    },
    {
        "id": "86e1f10557cab5ed",
        "type": "ui_group",
        "name": "temperature",
        "tab": "7f7bc8ca7693921c",
        "order": 1,
        "disp": true,
        "width": "6",
        "collapse": false,
        "className": ""
    },
    {
        "id": "641042f35d4db302",
        "type": "ui_group",
        "name": "Configuracion",
        "tab": "f10834acc0f1643e",
        "order": 1,
        "disp": true,
        "width": "6",
        "collapse": false,
        "className": ""
    },
    {
        "id": "79c7e6c65e0d3803",
        "type": "ui_group",
        "name": "History",
        "tab": "f10834acc0f1643e",
        "order": 2,
        "disp": true,
        "width": "6",
        "collapse": false,
        "className": ""
    },
    {
        "id": "7f7bc8ca7693921c",
        "type": "ui_tab",
        "name": "command",
        "icon": "dashboard",
        "disabled": false,
        "hidden": false
    },
    {
        "id": "f10834acc0f1643e",
        "type": "ui_tab",
        "name": "ProyectoIoT",
        "icon": "dashboard",
        "disabled": false,
        "hidden": false
    }
]
