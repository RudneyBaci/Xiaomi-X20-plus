# Xiaomi-X20-plus
Xiaomi X20 plus planning and room cleaning
Templates in configuration.yaml:

template:
  - sensor: 
    - name: "zonyvysavac"
      state: |-
        {%if states("input_boolean.spalnazonazapnut") == "on"%}1{%endif%}{%if states("input_boolean.kuchynazonazapnut") == "on"%}2{%endif%}{%if states("input_boolean.pracovnazonazapnut") == "on"%}3{%endif%}{%if states("input_boolean.zachodzonazapnut") == "on"%}4{%endif%}{%if states("input_boolean.kupelnazonazapnut") == "on"%}5{%endif%}{%if states("input_boolean.chodbazonazapnut") == "on"%}6{%endif%}{%if states("input_boolean.obyvackazonazapnut") == "on"%}7{%endif%}
      
input_boolean:
  pondelokvysavanie:
    name: "pondelok vysavanie"
    icon: mdi:broom
    initial: off
  pondelokzmyvanie:
    name: "pondelok umyvanie"
    icon: mdi:water
    initial: off
  pondelokvysavanieazmyvanie:
    name: "pondelok vysavanie a zmyvanie"
    icon: mdi:creation-outline
    initial: off
  utorokvysavanie:
    name: "utorok vysavanie"
    icon: mdi:broom
    initial: off
  utorokkzmyvanie:
    name: "utorok umyvanie"
    icon: mdi:water
    initial: off
  utorokvysavanieazmyvanie:
    name: "utorok vysavanie a zmyvanie"
    icon: mdi:creation-outline
    initial: off
  stredavysavanie:
    name: "streda vysavanie"
    icon: mdi:broom
    initial: off
  stredazmyvanie:
    name: "streda umyvanie"
    icon: mdi:water
    initial: off
  stredavysavanieazmyvanie:
    name: "streda vysavanie a zmyvanie"
    icon: mdi:creation-outline
    initial: off
  stvrtokvysavanie:
    name: "stvrtok vysavanie"
    icon: mdi:broom
    initial: off
  stvrtokzmyvanie:
    name: "stvrtok umyvanie"
    icon: mdi:water
    initial: off
  stvrtokvysavanieazmyvanie:
    name: "stvrtok vysavanie a zmyvanie"
    icon: mdi:creation-outline
    initial: off
  piatokvysavanie:
    name: "piatok vysavanie"
    icon: mdi:broom
    initial: off
  piatokzmyvanie:
    name: "piatok umyvanie"
    icon: mdi:water
    initial: off
  piatokvysavanieazmyvanie:
    name: "piatok vysavanie a zmyvanie"
    icon: mdi:creation-outline
    initial: off
  sobotavysavanie:
    name: "sobota vysavanie"
    icon: mdi:broom
    initial: off
  sobotazmyvanie:
    name: "sobota umyvanie"
    icon: mdi:water
    initial: off
  sobotavysavanieazmyvanie:
    name: "sobota vysavanie a zmyvanie"
    icon: mdi:creation-outline
    initial: off
  nedelavysavanie:
    name: "nedela vysavanie"
    icon: mdi:broom
    initial: off
  nedelazmyvanie:
    name: "nedela umyvanie"
    icon: mdi:water
    initial: off
  nedelavysavanieazmyvanie:
    name: "nedela vysavanie a zmyvanie"
    icon: mdi:creation-outline
    initial: off

automatization for cleaning:
alias: KasandraPlanovanie
description: ""
triggers:
  - trigger: time
    at: input_datetime.cas_pracovny_den
    id: Pracovnyden
  - trigger: time
    at: input_datetime.cas_vikend
    id: Vikend
conditions: []
actions:
  - sequence:
      - if:
          - condition: and
            conditions:
              - condition: time
                weekday:
                  - mon
              - condition: state
                entity_id: input_boolean.pondelok
                state: "on"
        then:
          - if:
              - condition: state
                entity_id: input_boolean.pondelokvysavanie
                state: "on"
            then:
              - action: script.vybrane_zony_povysavat
                data: {}
          - if:
              - condition: state
                entity_id: input_boolean.pondelokzmyvanie
                state: "on"
            then:
              - action: script.vybrane_zony_pozmyvat
                data: {}
          - if:
              - condition: state
                entity_id: input_boolean.pondelokvysavanieazmyvanie
                state: "on"
            then:
              - action: script.vybrane_zony_povysavat_a_pozmyvat
                data: {}
      - if:
          - condition: and
            conditions:
              - condition: time
                weekday:
                  - tue
              - condition: state
                entity_id: input_boolean.utorok
                state: "on"
        then:
          - if:
              - condition: state
                entity_id: input_boolean.utorokvysavanie
                state: "on"
            then:
              - action: script.vybrane_zony_povysavat
                data: {}
          - if:
              - condition: state
                entity_id: input_boolean.utorokkzmyvanie
                state: "on"
            then:
              - action: script.vybrane_zony_pozmyvat
                data: {}
          - if:
              - condition: state
                entity_id: input_boolean.utorokvysavanieazmyvanie
                state: "on"
            then:
              - action: script.vybrane_zony_povysavat_a_pozmyvat
                data: {}
      - if:
          - condition: and
            conditions:
              - condition: time
                weekday:
                  - wed
              - condition: state
                entity_id: input_boolean.streda
                state: "on"
        then:
          - if:
              - condition: state
                entity_id: input_boolean.stredavysavanie
                state: "on"
            then:
              - action: script.vybrane_zony_povysavat
                data: {}
          - if:
              - condition: state
                entity_id: input_boolean.stredazmyvanie
                state: "on"
            then:
              - action: script.vybrane_zony_pozmyvat
                data: {}
          - if:
              - condition: state
                entity_id: input_boolean.stredavysavanieazmyvanie
                state: "on"
            then:
              - action: script.vybrane_zony_povysavat_a_pozmyvat
                data: {}
      - if:
          - condition: and
            conditions:
              - condition: time
                weekday:
                  - thu
              - condition: state
                entity_id: input_boolean.stvrtok
                state: "on"
        then:
          - if:
              - condition: state
                entity_id: input_boolean.stvrtokvysavanie
                state: "on"
            then:
              - action: script.vybrane_zony_povysavat
                data: {}
          - if:
              - condition: state
                entity_id: input_boolean.stvrtokzmyvanie
                state: "on"
            then:
              - action: script.vybrane_zony_pozmyvat
                data: {}
          - if:
              - condition: state
                entity_id: input_boolean.stvrtokvysavanieazmyvanie
                state: "on"
            then:
              - action: script.vybrane_zony_povysavat_a_pozmyvat
                data: {}
      - if:
          - condition: and
            conditions:
              - condition: time
                weekday:
                  - fri
              - condition: state
                entity_id: input_boolean.piatok
                state: "on"
        then:
          - if:
              - condition: state
                entity_id: input_boolean.piatokvysavanie
                state: "on"
            then:
              - action: script.vybrane_zony_povysavat
                data: {}
          - if:
              - condition: state
                entity_id: input_boolean.piatokzmyvanie
                state: "on"
            then:
              - action: script.vybrane_zony_pozmyvat
                data: {}
          - if:
              - condition: state
                entity_id: input_boolean.piatokvysavanieazmyvanie
                state: "on"
            then:
              - action: script.vybrane_zony_povysavat_a_pozmyvat
                data: {}
      - if:
          - condition: and
            conditions:
              - condition: time
                weekday:
                  - sat
              - condition: state
                entity_id: input_boolean.sobota
                state: "on"
        then:
          - if:
              - condition: state
                entity_id: input_boolean.sobotavysavanie
                state: "on"
            then:
              - action: script.vybrane_zony_povysavat
                data: {}
          - if:
              - condition: state
                entity_id: input_boolean.sobotazmyvanie
                state: "on"
            then:
              - action: script.vybrane_zony_pozmyvat
                data: {}
          - if:
              - condition: state
                entity_id: input_boolean.sobotavysavanieazmyvanie
                state: "on"
            then:
              - action: script.vybrane_zony_povysavat_a_pozmyvat
                data: {}
      - if:
          - condition: and
            conditions:
              - condition: time
                weekday:
                  - sun
              - condition: state
                entity_id: input_boolean.nedela
                state: "on"
        then:
          - if:
              - condition: state
                entity_id: input_boolean.nedelavysavanie
                state: "on"
            then:
              - action: script.vybrane_zony_povysavat
                data: {}
          - if:
              - condition: state
                entity_id: input_boolean.nedelazmyvanie
                state: "on"
            then:
              - action: script.vybrane_zony_pozmyvat
                data: {}
          - if:
              - condition: state
                entity_id: input_boolean.nedelavysavanieazmyvanie
                state: "on"
            then:
              - action: script.vybrane_zony_povysavat_a_pozmyvat
                data: {}
mode: single

Script for vacuuming selected rooms: / just change vacuuming to mopping or vacuuming_and_mopping and create ones for mopping and vacuuming and mopping
sequence:
  - if:
      - condition: numeric_state
        entity_id: sensor.zonyvysavac
        below: 10
    then:
      - action: tts.speak
        metadata: {}
        data:
          cache: true
          media_player_entity_id: media_player.tab_a7_pouzivatela_rudolf
          message: >-
            Je potrebné vybrať aspoň dve lokácie pre vysávač, ak chceš vybrať
            len jednu lokáciu zvoľ funkciu v karte izby 
          language: sk
        target:
          entity_id: tts.google_translate_sk_sk
  - variables:
      segment: "{% for item in states(\"sensor.zonyvysavac\")%} {{item}}{% endfor %}"
  - action: switch.turn_on
    data: {}
    target:
      device_id: 55526f21c89daf26efce2fd42196cda5
  - action: select.select_option
    metadata: {}
    data:
      option: Roznavska
    target:
      entity_id: select.kasandra_selected_map
  - action: select.select_option
    metadata: {}
    data:
      option: sweeping
    target:
      entity_id: select.kasandra_room_1_cleaning_mode
  - action: select.select_option
    metadata: {}
    data:
      option: sweeping
    target:
      entity_id: select.kasandra_room_2_cleaning_mode
  - action: select.select_option
    metadata: {}
    data:
      option: sweeping
    target:
      entity_id: select.kasandra_room_3_cleaning_mode
  - action: select.select_option
    metadata: {}
    data:
      option: sweeping
    target:
      entity_id: select.kasandra_room_4_cleaning_mode
  - action: select.select_option
    metadata: {}
    data:
      option: sweeping
    target:
      entity_id: select.kasandra_room_5_cleaning_mode
  - action: select.select_option
    metadata: {}
    data:
      option: sweeping
    target:
      entity_id: select.kasandra_room_6_cleaning_mode
  - action: select.select_option
    metadata: {}
    data:
      option: sweeping
    target:
      entity_id: select.kasandra_room_7_cleaning_mode
  - action: dreame_vacuum.vacuum_clean_segment
    metadata: {}
    data:
      suction_level: 1
      segments: "{{segment.split(' ')}}"
    target:
      device_id: 55526f21c89daf26efce2fd42196cda5
alias: Vybrane zony povysavat
description: ""

Script for vacuuming just one room: / just change vacuuming to mopping or vacuuming_and_mopping and create ones for mopping and vacuuming and mopping
sequence:
  - action: switch.turn_on
    data: {}
    target:
      device_id: 55526f21c89daf26efce2fd42196cda5
  - action: select.select_option
    metadata: {}
    data:
      option: Roznavska
    target:
      entity_id: select.kasandra_selected_map
  - action: select.select_option
    metadata: {}
    data:
      option: sweeping
    target:
      entity_id: select.kasandra_room_6_cleaning_mode
  - action: select.select_option
    metadata: {}
    data:
      option: sweeping
    target:
      entity_id: select.kasandra_room_5_cleaning_mode
  - action: select.select_option
    metadata: {}
    data:
      option: sweeping
    target:
      entity_id: select.kasandra_room_4_cleaning_mode
  - action: dreame_vacuum.vacuum_clean_segment
    metadata: {}
    data:
      segments:
        - 5
        - 6
        - 4
      suction_level: 1
    target:
      device_id: 55526f21c89daf26efce2fd42196cda5
alias: Kasandra povysavat chodba
description: ""
