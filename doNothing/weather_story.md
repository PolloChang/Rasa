version: "3.1"
stories:
- story: happy path
    steps:
* request_weather
    - weather_form
    - form{"name": "weather_form"}
    - form{"name": null}
    
- story: happy path
    steps:
* greet
    - utter_answer_greet
* request_weather
    - weather_form
    - form{"name": "weather_form"}
    - form{"name": null}
* thanks
    - utter_noworries

- story: unhappy path
    steps:
* greet
    - utter_answer_greet
* request_weather
    - weather_form
    - form{"name": "weather_form"}
* chitchat
    - utter_chitchat
    - weather_form
    - form{"name": null}
* thanks
    - utter_noworries

- story: very unhappy path
    steps:
* greet
    - utter_answer_greet
* request_weather
    - weather_form
    - form{"name": "weather_form"}
* chitchat
    - utter_chitchat
    - weather_form
* chitchat
    - utter_chitchat
    - weather_form
* chitchat
    - utter_chitchat
    - weather_form
    - form{"name": null}
* thanks
    - utter_noworries

- story: stop but continue path
    steps:
* greet
    - utter_answer_greet
* request_weather
    - weather_form
    - form{"name": "weather_form"}
* stop
    - utter_ask_continue
* affirm
    - weather_form
    - form{"name": null}
* thanks
    - utter_noworries

- story: stop and really stop path
    steps:
* greet
    - utter_answer_greet
* request_weather
    - weather_form
    - form{"name": "weather_form"}
* stop
    - utter_ask_continue
* deny
    - action_deactivate_form
    - form{"name": null}

- story: chitchat stop but continue path
    steps:
* request_weather
    - weather_form
    - form{"name": "weather_form"}
* chitchat
    - utter_chitchat
    - weather_form
* stop
    - utter_ask_continue
* affirm
    - weather_form
    - form{"name": null}
* thanks
    - utter_noworries

- story: stop but continue and chitchat path
    steps:
* greet
    - utter_answer_greet
* request_weather
    - weather_form
    - form{"name": "weather_form"}
* stop
    - utter_ask_continue
* affirm
    - weather_form
* chitchat
    - utter_chitchat
    - weather_form
    - form{"name": null}
* thanks
    - utter_noworries

- story: chitchat stop but continue and chitchat path
    steps:
* greet
    - utter_answer_greet
* request_weather
    - weather_form
    - form{"name": "weather_form"}
* chitchat
    - utter_chitchat
    - weather_form
* stop
    - utter_ask_continue
* affirm
    - weather_form
* chitchat
    - utter_chitchat
    - weather_form
    - form{"name": null}
* thanks
    - utter_noworries

- story: chitchat, stop and really stop path
    steps:
* greet
    - utter_answer_greet
* request_weather
    - weather_form
    - form{"name": "weather_form"}
* chitchat
    - utter_chitchat
    - weather_form
* stop
    - utter_ask_continue
* deny
    - action_deactivate_form
    - form{"name": null}

# 天气 + 时间 + 地点 + 地点
- story: interactive_story_1
    steps:
* request_weather
    - weather_form
    - form{"name": "weather_form"}
    - slot{"requested_slot": "date_time"}
* form: inform{"date_time": "明天"}
    - form: weather_form
    - slot{"date_time": "明天"}
    - slot{"requested_slot": "address"}
* form: inform{"address": "广州"}
    - form: weather_form
    - slot{"address": "广州"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"date_time": "后天"} OR request_weather{"date_time": "后天"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "明天"}
    - slot{"address": "广州"}
    - slot{"date_time": "后天"}
    - form{"name": null}
    - slot{"requested_slot": null}
* thanks
    - utter_answer_thanks

# 天气 + 时间 + 地点 + 时间
- story: interactive_story_1
    steps:
* request_weather
    - weather_form
    - form{"name": "weather_form"}
    - slot{"requested_slot": "date_time"}
* form: inform{"date_time": "明天"}
    - form: weather_form
    - slot{"date_time": "明天"}
    - slot{"requested_slot": "address"}
* form: inform{"address": "广州"}
    - form: weather_form
    - slot{"address": "广州"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"address": "上海"} OR request_weather{"address": "深圳"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "明天"}
    - slot{"address": "广州"}
    - slot{"address": "上海"}
    - form{"name": null}
    - slot{"requested_slot": null}
* affirm
    - utter_answer_affirm

# 天气/时间/地点 + 地点
- story: interactive_story_2
    steps:
* request_weather{"date_time": "明天", "address": "上海"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "明天"}
    - slot{"address": "上海"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"address": "广州"} OR request_weather{"address": "广州"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "明天"}
    - slot{"address": "上海"}
    - slot{"address": "广州"}
    - form{"name": null}
    - slot{"requested_slot": null}
* thanks
    - utter_answer_thanks

# 天气/时间/地点 + 时间
- story: interactive_story_3
    steps:
* request_weather{"address": "深圳", "date_time": "后天"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "后天"}
    - slot{"address": "深圳"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"date_time": "大后天"} OR request_weather{"date_time": "大后天"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "后天"}
    - slot{"address": "深圳"}
    - slot{"date_time": "大后天"}
    - form{"name": null}
    - slot{"requested_slot": null}
* thanks
    - utter_answer_thanks

# 天气/时间/地点 + 地点 + 时间
- story: interactive_story_2
    steps:
* request_weather{"date_time": "明天", "address": "上海"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "明天"}
    - slot{"address": "上海"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"address": "北京"} OR request_weather{"address": "北京"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "明天"}
    - slot{"address": "上海"}
    - slot{"address": "北京"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"date_time": "后天"} OR request_weather{"date_time": "后天"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "明天"}
    - slot{"address": "北京"}
    - slot{"date_time": "后天"}
    - form{"name": null}
    - slot{"requested_slot": null}
* affirm
    - utter_answer_affirm

# 天气/时间/地点 + 地点 + 地点
- story: interactive_story_3
    steps:
* request_weather{"date_time": "后天", "address": "北京"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "后天"}
    - slot{"address": "北京"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"address": "深圳"} OR request_weather{"address": "深圳"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "后天"}
    - slot{"address": "北京"}
    - slot{"address": "深圳"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"address": "南京"} OR request_weather{"address": "南京"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "后天"}
    - slot{"address": "深圳"}
    - slot{"address": "南京"}
    - form{"name": null}
    - slot{"requested_slot": null}
* thanks
    - utter_answer_thanks

# 天气/时间/地点 + 时间 + 地点
- story: interactive_story_4
    steps:
* request_weather{"date_time": "明天", "address": "长沙"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "明天"}
    - slot{"address": "长沙"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"date_time": "后天"} OR request_weather{"date_time": "后天"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "明天"}
    - slot{"address": "长沙"}
    - slot{"date_time": "后天"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"date_time": "大后天"} OR request_weather{"date_time": "大后天"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "后天"}
    - slot{"address": "长沙"}
    - slot{"date_time": "大后天"}
    - form{"name": null}
    - slot{"requested_slot": null}
* affirm
    - utter_answer_affirm

# 天气/时间/地点 + 时间 + 时间
- story: interactive_story_5
    steps:
* request_weather{"date_time": "后天", "address": "深圳"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "后天"}
    - slot{"address": "深圳"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"date_time": "明天"} OR request_weather{"date_time": "明天"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "后天"}
    - slot{"address": "深圳"}
    - slot{"date_time": "明天"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"address": "广州"} OR request_weather{"address": "广州"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "明天"}
    - slot{"address": "深圳"}
    - slot{"address": "广州"}
    - form{"name": null}
    - slot{"requested_slot": null}
* thanks
    - utter_answer_thanks

# 天气/时间 + 地点 + 时间
- story: interactive_story_4
    steps:
* request_weather{"date_time": "明天"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "明天"}
    - slot{"requested_slot": "address"}
* form: inform{"address": "广州"}
    - form: weather_form
    - slot{"address": "广州"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"date_time": "后天"} OR request_weather{"date_time": "后天"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "明天"}
    - slot{"address": "广州"}
    - slot{"date_time": "后天"}
    - form{"name": null}
    - slot{"requested_slot": null}
* thanks
    - utter_answer_thanks

# 天气/地点 + 时间 + 时间
- story: interactive_story_5
    steps:
* request_weather{"address": "广州"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"address": "广州"}
    - slot{"requested_slot": "date_time"}
* form: inform{"date_time": "后天"}
    - form: weather_form
    - slot{"date_time": "后天"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"date_time": "明天"} OR request_weather{"date_time": "明天"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "后天"}
    - slot{"address": "广州"}
    - slot{"date_time": "明天"}
    - form{"name": null}
    - slot{"requested_slot": null}
* thanks
    - utter_answer_thanks
    
# 天气/时间/地点 + chit + chit(restart)+询问天气
- story: interactive_story_1
    steps:
* request_weather{"date_time": "今天", "address": "广州"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "今天"}
    - slot{"address": "广州"}
    - form{"name": null}
    - slot{"requested_slot": null}
* chitchat
    - utter_chitchat
* chitchat
    - utter_chitchat
    - action_restart
* request_weather
    - weather_form
    - form{"name": "weather_form"}
    - slot{"requested_slot": "date_time"}
* form: inform{"date_time": "今天"}
    - form: weather_form
    - slot{"date_time": "今天"}
    - slot{"requested_slot": "address"}
* form: inform{"address": "广州"}
    - form: weather_form
    - slot{"address": "广州"}
    - form{"name": null}
    - slot{"requested_slot": null}
* thanks
    - utter_answer_thanks