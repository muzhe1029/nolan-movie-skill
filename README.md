# nolan-movie-skill
融合诺兰时间操控与盖里奇多线巧合的电影语言生成技能包，输出分镜脚本、剪辑方案、声音设计、拍摄提示词。

目录结构

nolan-movie-skill/
├── skill.yaml                 # 主 skill 定义（入口）
├── README.md                  # 使用说明
├── core/
│   ├── master_prompt.md       # 主提示词/拍摄手法总纲
│   └── templates/
│       ├── shot_script.md
│       ├── edit_script.md
│       └── sound_script.md
├── atoms/
│   ├── narrative/
│   │   ├── time_linear.md
│   │   ├── time_reverse.md
│   │   ├── nested_dream.md
│   │   ├── palindrome.md
│   │   ├── multi_thread_coincidence.md
│   │   └── loop.md
│   ├── editing/
│   │   ├── cross_cutting.md
│   │   ├── parallel_montage.md
│   │   ├── reverse_playback.md
│   │   ├── match_cut.md
│   │   ├── freeze_frame.md
│   │   └── title_card.md
│   ├── camera/
│   │   ├── imax_real.md
│   │   ├── subjective_pov.md
│   │   ├── symmetry.md
│   │   ├── low_angle.md
│   │   ├── rotate_shot.md
│   │   └── long_take.md
│   ├── sound/
│   │   ├── pulse_bass.md
│   │   ├── shepard_tone.md
│   │   ├── reverse_audio.md
│   │   └── dialogue_rapid.md
│   └── color/
│       ├── cold_tone.md
│       ├── low_saturation.md
│       └── high_contrast.md
├── memory/
│   ├── feedback_log.md
│   ├── version_history.md
│   └── user_preferences.json
└── examples/
    ├── memento_style.md
    ├── inception_style.md
    ├── tenet_style.md
    ├── odyssey_style.md
    └── lock_stock_style.md
