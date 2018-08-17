A tool to decode yizhibo chat flow.

A chat message in Yizhibo app (version > 1.9) is constructed as flowing:

Message head:

    ```
    \x00 \x00 \x00 \x65 \x00 \x00 \x00 \x02
    |----fixed 0x65---| |--message type---|
    
    \xff \xff \xff \xfe or \x00 \x00 \x00 \x00
    |fixed in auth msg|    |fixed in regular msg|
    
    \x00 \x00 \x00 \x5c
    |-message body length--|
    
    Message Body: encoded with protobuf
    \x.......
    |message body|
    ```

# protobuf-decoder

This is a protobuf-decoder which can decode protobuf binary file without .proto files. It supports editing to the decoded file and re-encoding to a bianry file. It can also work as a brup plugin.

## Have a try

1. `python parse.py yizhibo_flow`

    Now you can see the decoded field looks like:
    
    ```
    [
        {
            "_command": 2,
            "body": {
                "01:00:Varint": 342958069,
                "02:01:string": "1qsluLDy2VThob84",
                "03:02:string": "4d62c8ac9c959dfdd2d49245eb57caa2",
                "04:03:string": "57e3f85dc85b67a49c14a613460f8f68"
            }
        },
        {
            "_command": 2,
            "body": {}
        },
        {
            "_command": 601,
            "body": {
                "01:00:Varint": 355595162,
                "05:01:string": "1qsluLDy2VThob84",
                "10:02:Varint": 5251,
                "11:03:Varint": 5300,
                "25:04:string": "1534228069127"
            }
        },
        {
            "_command": 600,
            "body": {
                "01:00:string": "1qsluLDy2VThob84",
                "02:01:string": "342958069",
                "03:02:string": "https://tvax3.sinaimg.cn/crop.0.0.1440.1440.50/006AzkE5ly8fhel2zyzccj314014045f.jpg",
                "05:03:Varint": 4,
                "06:04:string": "oぃ我愛了壹個曾經ヤ︎",
                "07:05:string": "普通",
                "10:06:Varint": 1,
                "13:07:Varint": 4074,
                "16:08:Varint": 5252,
                "17:09:Varint": 6184,
                "18:10:string": "6037165933",
                "19:11:string": "1025343130",
                "20:12:Varint": 1,
                "23:13:string": "1534228069184",
                "26:14:string": "356257955,240798196,46936482"
            }
        },
        {
            "_command": 1102,
            "body": {
                "01:00:Varint": 58838,
                "02:01:Varint": 226,
                "03:02:Varint": 5305,
                "04:03:Varint": 7440,
                "05:04:Varint": 5252,
                "06:05:Varint": 1534223754,
                "08:06:Varint": 6184,
                "09:07:Varint": 2388,
                "10:08:string": "1qsluLDy2VThob84",
                "11:09:Varint": 10,
                "14:10:string": "1534228069194"
            }
        },
        {
            "_command": 200,
            "body": {
                "01:00:string": "1qsluLDy2VThob84",
                "02:01:Varint": 3062,
                "04:02:string": "Vermouthmt2p0",
                "05:03:string": "http://q.qlogo.cn/qqapp/1104915773/2774A11CDA5A3AC9E4891FD6ED69058B/40",
                "06:04:string": "244819590",
                "07:05:Varint": 8,
                "09:06:Varint": 14900,
                "10:07:Varint": 2,
                "17:08:Varint": 2,
                "20:09:Varint": 478125398,
                "22:10:string": "1534228069699"
            }
        },
        {
            "_command": 601,
            "body": {
                "01:00:Varint": 47776317,
                "03:01:string": "https://alcdn.img.xiaoka.tv/20161224/b53/951/0/b539515e27e7015060b444591a4850bf.jpg@1e_1c_0o_0l_160h_160w_100q_1pr.jpg",
                "05:02:string": "1qsluLDy2VThob84",
                "06:03:Varint": 1,
                "07:04:Varint": 1,
                "10:05:Varint": 5251,
                "11:06:Varint": 5296,
                "14:07:64-bit": 1.0,
                "23:08:Varint": 1,
                "25:09:string": "1534228070047"
            }
        },
        {
            "_command": 600,
            "body": {
                "01:00:string": "1qsluLDy2VThob84",
                "02:01:string": "26593968",
                "03:02:string": "https://alcdn.img.xiaoka.tv/20161224/d53/601/0/d5360170c7b9c493671632f94d69fd32.jpg?x-oss-process=image/resize,m_fixed,h_72,w_72",
                "05:03:Varint": 1,
                "06:04:string": "不离不弃8543",
                "10:05:Varint": 1,
                "16:06:Varint": 5253,
                "17:07:Varint": 5298,
                "19:08:string": "1",
                "20:09:Varint": 1,
                "23:10:string": "1534228070063"
            }
        },
        {
            "_command": 600,
            "body": {
                "01:00:string": "1qsluLDy2VThob84",
                "02:01:string": "6709067",
                "03:02:string": "https://wscdn.miaopai.com/xkx4/2016/0512/90e4da674da3fbc4794b6ef47805cd9d.jpg",
                "05:03:Varint": 1,
                "06:04:string": "想逛逛天涯",
                "10:05:Varint": 1,
                "16:06:Varint": 5253,
                "17:07:Varint": 5298,
                "19:08:string": "1",
                "20:09:Varint": 2,
                "23:10:string": "1534228070229"
            }
        },
        {
            "_command": 601,
            "body": {
                "01:00:Varint": 24935151,
                "03:01:string": "https://alcdn.img.xiaoka.tv/20161224/cf4/b16/0/cf4b163fb778df4be45582efab8f907c.jpg@1e_1c_0o_0l_160h_160w_100q_1pr.jpg",
                "05:02:string": "1qsluLDy2VThob84",
                "06:03:Varint": 1,
                "07:04:Varint": 1,
                "10:05:Varint": 5251,
                "11:06:Varint": 5296,
                "14:07:64-bit": 1.0,
                "23:08:Varint": 1,
                "25:09:string": "1534228070279"
            }
        },
        {
            "_command": 600,
            "body": {
                "01:00:string": "1qsluLDy2VThob84",
                "02:01:string": "61598021",
                "03:02:string": "https://alcdn.img.xiaoka.tv/20161229/6ce/187/0/6ce187b58557cd0c14601c00dc670624.jpg?x-oss-process=image/resize,m_fixed,h_72,w_72",
                "05:03:Varint": 1,
                "06:04:string": "木鱼1333",
                "10:05:Varint": 1,
                "16:06:Varint": 5253,
                "17:07:Varint": 5298,
                "19:08:string": "1",
                "20:09:Varint": 2,
                "23:10:string": "1534228070297"
            }
        },
        {
            "_command": 600,
            "body": {
                "01:00:string": "1qsluLDy2VThob84",
                "02:01:string": "245195827",
                "03:02:string": "https://tva3.sinaimg.cn/crop.0.0.100.100.180/0068yKu4jw8esq7jnuuxjj302s02s743.jpg",
                "05:03:Varint": 1,
                "06:04:string": "晓丿锦",
                "07:05:string": "普通",
                "10:06:Varint": 1,
                "13:07:Varint": 250,
                "16:08:Varint": 5233,
                "17:09:Varint": 6165,
                "18:10:string": "5623289520",
                "19:11:string": "1022751129",
                "20:12:Varint": 1,
                "23:13:string": "1534228070921",
                "26:14:string": "356257955,240798196,46936482"
            }
        },
        {
            "_command": 1102,
            "body": {
                "01:00:Varint": 58875,
                "02:01:Varint": 226,
                "03:02:Varint": 5305,
                "04:03:Varint": 7450,
                "05:04:Varint": 5233,
                "06:05:Varint": 1534223754,
                "08:06:Varint": 6165,
                "09:07:Varint": 2388,
                "10:08:string": "1qsluLDy2VThob84",
                "11:09:Varint": 10,
                "14:10:string": "1534228070932"
            }
        },
        {
            "_command": 600,
            "body": {
                "01:00:string": "1qsluLDy2VThob84",
                "02:01:string": "355835028",
                "03:02:string": "https://alcdn.img.xiaoka.tv/20180814/ab7/735/355835028/ab773507ff73d5cf7a78d51321fabe1e.jpg?x-oss-process=image/resize,m_fixed,h_72,w_72",
                "05:03:Varint": 3,
                "06:04:string": "★冬悸メ雪曲，@梦莹",
                "07:05:string": "普通",
                "10:06:Varint": 1,
                "13:07:Varint": 1319,
                "16:08:Varint": 5234,
                "17:09:Varint": 6166,
                "19:10:string": "1024479128",
                "20:11:Varint": 2,
                "23:12:string": "1534228071206",
                "26:13:string": "356257955,240798196,46936482",
                "30:14:Varint": 4
            }
        },
        {
            "_command": 1102,
            "body": {
                "01:00:Varint": 58876,
                "02:01:Varint": 226,
                "03:02:Varint": 5305,
                "04:03:Varint": 7450,
                "05:04:Varint": 5234,
                "06:05:Varint": 1534223754,
                "08:06:Varint": 6166,
                "09:07:Varint": 2388,
                "10:08:string": "1qsluLDy2VThob84",
                "11:09:Varint": 10,
                "14:10:string": "1534228071214"
            }
        },
        {
            "_command": 601,
            "body": {
                "01:00:Varint": 354629306,
                "05:01:string": "1qsluLDy2VThob84",
                "10:02:Varint": 5233,
                "11:03:Varint": 5282,
                "25:04:string": "1534228073044"
            }
        },
        {
            "_command": 300,
            "body": {
                "01:00:string": "1qsluLDy2VThob84",
                "02:01:Varint": 8,
                "07:02:string": "Vermouthmt2p0",
                "08:03:string": "送了1个",
                "09:04:string": "https://alcdn.img.xiaoka.tv/20180315/f61/f17/0/f61f174e1029c8f175a5ec988d48f436.png",
                "10:05:string": "244819590",
                "15:06:Varint": 2,
                "16:07:string": "#000000",
                "17:08:32-bit": 0.30000001192092896,
                "18:09:string": "#FFD88C",
                "19:10:string": "#FFD88C",
                "22:11:Varint": 10,
                "24:12:string": "http://q.qlogo.cn/qqapp/1104915773/2774A11CDA5A3AC9E4891FD6ED69058B/40",
                "25:13:string": "1534228073777",
                "27:14:string": "送了1个"
            }
        },
        {
            "_command": 600,
            "body": {
                "01:00:string": "1qsluLDy2VThob84",
                "02:01:embedded message": {
                    "06:00:64-bit": 1.1996598566308456e-71
                },
                "03:02:string": "https://alcdn.img.xiaoka.tv/20180111/a8d/5c0/187467251/a8d5c0a26d8a8d87004d8d82cd1e6e68.jpg?x-oss-process=image/resize,m_fixed,h_72,w_72",
                "05:03:Varint": 11,
                "06:04:string": "🇨🇳绵绵💙人直",
                "07:05:string": "普通",
                "10:06:Varint": 1,
                "13:07:Varint": 509069,
                "16:08:Varint": 5234,
                "17:09:Varint": 6166,
                "18:10:string": "6095054429",
                "19:11:string": "1031391125",
                "20:12:Varint": 1,
                "23:13:string": "1534228074109",
                "26:14:string": "356257955,240798196,46936482"
            }
        },
        {
            "_command": 1102,
            "body": {
                "01:00:Varint": 58877,
                "02:01:Varint": 226,
                "03:02:Varint": 5305,
                "04:03:Varint": 7450,
                "05:04:Varint": 5234,
                "06:05:Varint": 1534223754,
                "08:06:Varint": 6166,
                "09:07:Varint": 2388,
                "10:08:string": "1qsluLDy2VThob84",
                "11:09:Varint": 10,
                "14:10:string": "1534228074118"
            }
        },
        {
            "_command": 601,
            "body": {
                "01:00:Varint": 33063725,
                "05:01:string": "1qsluLDy2VThob84",
                "10:02:Varint": 5233,
                "11:03:Varint": 5282,
                "25:04:string": "1534228074353"
            }
        },
        {
            "_command": 300,
            "body": {
                "01:00:string": "1qsluLDy2VThob84",
                "02:01:Varint": 2,
                "07:02:string": "我的爱人在河处1v8h0m81f4",
                "08:03:string": "关注了主播",
                "10:04:string": "356344778",
                "15:05:Varint": 2,
                "16:06:string": "#000000",
                "17:07:32-bit": 0.30000001192092896,
                "18:08:string": "#FFD88C",
                "19:09:string": "#FFD88C",
                "22:10:Varint": 8,
                "24:11:string": "http://thirdqq.qlogo.cn/qqapp/1104915773/F9A5547BE6D38ECE2196BE139CBDE584/40",
                "25:12:string": "1534228074444832",
                "27:13:string": "关注了主播"
            }
        },
        {
            "_command": 601,
            "body": {
                "01:00:Varint": 355740370,
                "05:01:string": "1qsluLDy2VThob84",
                "10:02:Varint": 5232,
                "11:03:Varint": 5281,
                "25:04:string": "1534228075034"
            }
        },
        {
            "_command": 601,
            "body": {
                "01:00:Varint": 61598021,
                "03:01:string": "https://alcdn.img.xiaoka.tv/20161229/6ce/187/0/6ce187b58557cd0c14601c00dc670624.jpg@1e_1c_0o_0l_160h_160w_100q_1pr.jpg",
                "05:02:string": "1qsluLDy2VThob84",
                "06:03:Varint": 2,
                "07:04:Varint": 1,
                "10:05:Varint": 5231,
                "11:06:Varint": 5296,
                "14:07:64-bit": 1.0,
                "23:08:Varint": 1,
                "25:09:string": "1534228075223"
            }
        },
        {
            "_command": 601,
            "body": {
                "01:00:Varint": 110264577,
                "05:01:string": "1qsluLDy2VThob84",
                "10:02:Varint": 5225,
                "11:03:Varint": 5274,
                "25:04:string": "1534228077181"
            }
        },
        {
            "_command": 601,
            "body": {
                "01:00:Varint": 342958069,
                "05:01:string": "1qsluLDy2VThob84",
                "10:02:Varint": 5224,
                "11:03:Varint": 5273,
                "25:04:string": "1534228077346"
            }
        }
    ]
    ```