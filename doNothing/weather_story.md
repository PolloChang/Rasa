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

# ?????? + ?????? + ?????? + ??????
- story: interactive_story_1
    steps:
* request_weather
    - weather_form
    - form{"name": "weather_form"}
    - slot{"requested_slot": "date_time"}
* form: inform{"date_time": "??????"}
    - form: weather_form
    - slot{"date_time": "??????"}
    - slot{"requested_slot": "address"}
* form: inform{"address": "??????"}
    - form: weather_form
    - slot{"address": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"date_time": "??????"} OR request_weather{"date_time": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
    - slot{"date_time": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* thanks
    - utter_answer_thanks

# ?????? + ?????? + ?????? + ??????
- story: interactive_story_1
    steps:
* request_weather
    - weather_form
    - form{"name": "weather_form"}
    - slot{"requested_slot": "date_time"}
* form: inform{"date_time": "??????"}
    - form: weather_form
    - slot{"date_time": "??????"}
    - slot{"requested_slot": "address"}
* form: inform{"address": "??????"}
    - form: weather_form
    - slot{"address": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"address": "??????"} OR request_weather{"address": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
    - slot{"address": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* affirm
    - utter_answer_affirm

# ??????/??????/?????? + ??????
- story: interactive_story_2
    steps:
* request_weather{"date_time": "??????", "address": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"address": "??????"} OR request_weather{"address": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
    - slot{"address": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* thanks
    - utter_answer_thanks

# ??????/??????/?????? + ??????
- story: interactive_story_3
    steps:
* request_weather{"address": "??????", "date_time": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"date_time": "?????????"} OR request_weather{"date_time": "?????????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
    - slot{"date_time": "?????????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* thanks
    - utter_answer_thanks

# ??????/??????/?????? + ?????? + ??????
- story: interactive_story_2
    steps:
* request_weather{"date_time": "??????", "address": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"address": "??????"} OR request_weather{"address": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
    - slot{"address": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"date_time": "??????"} OR request_weather{"date_time": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
    - slot{"date_time": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* affirm
    - utter_answer_affirm

# ??????/??????/?????? + ?????? + ??????
- story: interactive_story_3
    steps:
* request_weather{"date_time": "??????", "address": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"address": "??????"} OR request_weather{"address": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
    - slot{"address": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"address": "??????"} OR request_weather{"address": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
    - slot{"address": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* thanks
    - utter_answer_thanks

# ??????/??????/?????? + ?????? + ??????
- story: interactive_story_4
    steps:
* request_weather{"date_time": "??????", "address": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"date_time": "??????"} OR request_weather{"date_time": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
    - slot{"date_time": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"date_time": "?????????"} OR request_weather{"date_time": "?????????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
    - slot{"date_time": "?????????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* affirm
    - utter_answer_affirm

# ??????/??????/?????? + ?????? + ??????
- story: interactive_story_5
    steps:
* request_weather{"date_time": "??????", "address": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"date_time": "??????"} OR request_weather{"date_time": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
    - slot{"date_time": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"address": "??????"} OR request_weather{"address": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
    - slot{"address": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* thanks
    - utter_answer_thanks

# ??????/?????? + ?????? + ??????
- story: interactive_story_4
    steps:
* request_weather{"date_time": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"requested_slot": "address"}
* form: inform{"address": "??????"}
    - form: weather_form
    - slot{"address": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"date_time": "??????"} OR request_weather{"date_time": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
    - slot{"date_time": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* thanks
    - utter_answer_thanks

# ??????/?????? + ?????? + ??????
- story: interactive_story_5
    steps:
* request_weather{"address": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"address": "??????"}
    - slot{"requested_slot": "date_time"}
* form: inform{"date_time": "??????"}
    - form: weather_form
    - slot{"date_time": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* inform{"date_time": "??????"} OR request_weather{"date_time": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
    - slot{"date_time": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* thanks
    - utter_answer_thanks
    
# ??????/??????/?????? + chit + chit(restart)+????????????
- story: interactive_story_1
    steps:
* request_weather{"date_time": "??????", "address": "??????"}
    - weather_form
    - form{"name": "weather_form"}
    - slot{"date_time": "??????"}
    - slot{"address": "??????"}
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
* form: inform{"date_time": "??????"}
    - form: weather_form
    - slot{"date_time": "??????"}
    - slot{"requested_slot": "address"}
* form: inform{"address": "??????"}
    - form: weather_form
    - slot{"address": "??????"}
    - form{"name": null}
    - slot{"requested_slot": null}
* thanks
    - utter_answer_thanks