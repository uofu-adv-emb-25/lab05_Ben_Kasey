# Lab 05
Status Badge: ![Lab05 Status](https://github.com/uofu-adv-emb-25/lab05_Ben_Kasey/actions/workflows/main.yml/badge.svg)

By Ben Martins and Kasey Kemp


## Activity 1:
sleep.c: 
    | Starting Time Offset | After 5 mins | Extrapolated Drift |
    | 97.1044 ms | 94.2958 ms | 33.7032 ms/hour |

    | Type | Min | Max | Mean | StdDev | Wave Count |
    | Period | 199.9996 ms | 200.0027 ms | 200.0027 ms | 1.302 us | 268 |
    | Frequency | 4.99996 Hz | 5.00003 Hz | 4.99996 Hz | 35.1 uHz | 85 |
    | Duty-Cycle | 50.00 % | 50.00 % | 50.00 % | 0.00 % | 74 |

rts.c:
    | Starting Time Offset | After 5 mins | Extrapolated Drift |
    | 472.16 ms | 475.2 ms | -36.48 ms/hour |

    | Type | Min | Max | Mean | StdDev | Wave Count |
    | Period | 1.999998 s | 1.999998s s | 1.999998 s | 0 s | 80 |
    | Frequency | 500.002 mHz | 500.002 mHz | 500.001 mHz | 0 Hz | 80 |
    | Duty-Cycle | 50.00 % | 50.00 % | 50.00 % | 0.00 % | 80 |

task_delay.c
    | Starting Time Offset | After 5 mins | Extrapolated Drift |
    | 52.2698 ms | 55.1908 ms | 35.052 ms/hour |

    | Type | Min | Max | Mean | StdDev | Wave Count |
    | Period | 200.0034 ms | 200.0034 ms | 200.0034 ms | 46 ns | 834 |
    | Frequency | 4.99993 Hz | 4.99993 Hz | 4.99996 Hz | 1.14 uHz | 834 |
    | Duty-Cycle | 50.00 % | 50.00 % | 50.00 % | 0.00 % | 834 |

timer.c
    | Starting Time Offset | After 5 mins | Extrapolated Drift |
    | 41.3362 ms | 44.239 ms | -34.8336 ms/hour |

    | Type | Min | Max | Mean | StdDev | Wave Count |
    | Period | 199.998 ms | 199.998 ms | 199.998 ms | 0s ns | 265 |
    | Frequency | 4.99999 Hz | 4.99999 Hz | 4.99999 Hz | 410 uHz | 265 |
    | Duty-Cycle | 50.00 % | 50.00 % | 50.00 % | 0.00 % | 265 |

### Adding Busy Loop (100,000 loops)
sleep.c: 
    | Starting Time Offset | After 5 mins | Extrapolated Drift |
    | 60.1142 ms | -57.3262 ms | 1,409.2848 ms/hour |

    | Type | Min | Max | Mean | StdDev | Wave Count |
    | Period | 200.08 ms | 200.08 ms | 200.08 ms | 0 s | 253 |
    | Frequency | 4.99798 Hz | 4.99798 Hz | 4.99798 Hz | 0 Hz | 253 |
    | Duty-Cycle | 50.00 % | 50.00 % | 50.00 % | 0.00 % | 74 |

rts.c:
    | Starting Time Offset | After 5 mins | Extrapolated Drift |
    | 378.336 ms | 383.04 ms | -56.448 ms/hour |

    | Type | Min | Max | Mean | StdDev | Wave Count |
    | Period | 1.999998 s | 1.999998s s | 1.999998 s | 210 s | 123 |
    | Frequency | 499.997 mHz | 499.997 mHz | 499.997 mHz | 53 nHz | 123 |
    | Duty-Cycle | 50.00 % | 50.00 % | 50.00 % | 0.00 % | 123 |

task_delay.c
    Timing is off by too much to get an accurate delay reading. However, extrapolating using the frequency, the estimated drift would be 28.8 s/hour.

    | Type | Min | Max | Mean | StdDev | Wave Count |
    | Period | 208.0012 ms | 208.00312 ms | 208.0012 ms | 0 s | 129 |
    | Frequency | 4.80772 Hz | 4.80772 Hz | 4.80772 Hz | 0 Hz | 129 |
    | Duty-Cycle | 50.00 % | 50.00 % | 50.00 % | 0.00 % | 129 |

timer.c
    | Starting Time Offset | After 5 mins | Extrapolated Drift |
    | -29.8972 ms | -27.0846 ms | -33.7512 ms/hour |

    | Type | Min | Max | Mean | StdDev | Wave Count |
    | Period | 199.998 ms | 199.998 ms | 199.998 ms | 0s ns | 258 |
    | Frequency | 4.99999 Hz | 4.99999 Hz | 4.99999 Hz | 410 uHz | 258 |
    | Duty-Cycle | 50.00 % | 50.00 % | 50.00 % | 0.00 % | 265 |

## Activity 2:
Measuring Delay of GPIO Interrupt:
| Interrupt Handler | Mean Delay | Max Delay |
| Normal | 0 s | 4.6 us |
| Busy Loop | 3.9974 ms | 4.002 ms |

| Syntax | Description |
| --- | ----------- |
| Header | Title |
| Paragraph | Text |