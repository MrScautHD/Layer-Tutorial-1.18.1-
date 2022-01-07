# Layer Tutorial 1.18.1

(MANY IDS NAMED BY MY OWN MOD, Example: "beyond_earth:glacio", just change it to your ids)

BEDROCK LAYER (you need a Custom Chunk Generator to fix caves (Noodle caves...) generate in the bedrock):

```json
          {
            "type": "minecraft:condition",
            "if_true": {
              "type": "minecraft:vertical_gradient",
              "random_name": "minecraft:bedrock_floor",
              "true_at_and_below": {
                "above_bottom": 0
              },
              "false_at_and_above": {
                "above_bottom": 5
              }
            },
            "then_run": {
              "type": "minecraft:block",
              "result_state": {
                "Name": "minecraft:bedrock"
              }
            }
          }
```

TOP LAYER:


```json
          {
            "type": "minecraft:condition",
            "if_true": {
              "type": "minecraft:biome",
              "biome_is": [
                "beyond_earth:glacio",
                "beyond_earth:glacio_ice_spikes"
              ]
            },
            "then_run": {
              "type": "minecraft:condition",
              "if_true": {
                "type": "minecraft:y_above",
                "anchor": {
                  "absolute": 87
                },
                "surface_depth_multiplier": 2,
                "add_stone_depth": false
              },
              "then_run": {
                "type": "minecraft:condition",
                "if_true": {
                  "type": "minecraft:water",
                  "offset": -2,
                  "surface_depth_multiplier": 0,
                  "add_stone_depth": false
                },
                "then_run": {
                  "type": "minecraft:sequence",
                  "sequence": [
                    {
                      "type": "minecraft:condition",
                      "if_true": {
                        "type": "minecraft:stone_depth",
                        "offset": 1,
                        "surface_type": "floor",
                        "add_surface_depth": false,
                        "add_surface_secondary_depth": false
                      },
                      "then_run": {
                        "type": "minecraft:block",
                        "result_state": {
                          "Name": "minecraft:snow_block"
                        }
                      }
                    }
                  ]
                }
              }
            }
          }
```

TOP LAYER WITH SANDSTONE LAYER:

```json
          {
            "type": "minecraft:condition",
            "if_true": {
              "type": "minecraft:biome",
              "biome_is": [
                "beyond_earth:glacio",
                "beyond_earth:glacio_ice_spikes"
              ]
            },
            "then_run": {
              "type": "minecraft:condition",
              "if_true": {
                "type": "minecraft:y_above",
                "anchor": {
                  "absolute": 87
                },
                "surface_depth_multiplier": 2,
                "add_stone_depth": false
              },
              "then_run": {
                "type": "minecraft:condition",
                "if_true": {
                  "type": "minecraft:water",
                  "offset": -2,
                  "surface_depth_multiplier": 0,
                  "add_stone_depth": false
                },
                "then_run": {
                  "type": "minecraft:sequence",
                  "sequence": [
                    {
                      "type": "minecraft:condition",
                      "if_true": {
                        "type": "minecraft:stone_depth",
                        "offset": 1,
                        "surface_type": "floor",
                        "add_surface_depth": false,
                        "add_surface_secondary_depth": false
                      },
                      "then_run": {
                        "type": "minecraft:block",
                        "result_state": {
                          "Name": "minecraft:snow_block"
                        }
                      }
                    },
                    {
                      "type": "minecraft:block",
                      "result_state": {
                        "Name": "minecraft:packed_ice"
                      }
                    }
                  ]
                }
              }
            }
          }
```

POWDER SNOW:
```json
          {
            "type": "minecraft:condition",
            "if_true": {
              "type": "minecraft:biome",
              "biome_is": [
                "beyond_earth:glacio",
                "beyond_earth:glacio_ice_spikes"
              ]
            },
            "then_run": {
              "type": "minecraft:sequence",
              "sequence": [
                {
                  "type": "minecraft:condition",
                  "if_true": {
                    "type": "minecraft:noise_threshold",
                    "noise": "minecraft:powder_snow",
                    "min_threshold": 0.35,
                    "max_threshold": 0.6
                  },
                  "then_run": {
                    "type": "minecraft:block",
                    "result_state": {
                      "Name": "minecraft:powder_snow"
                    }
                  }
                }
              ]
            }
          },
```

DEEPSLATE LAYER:

```json
          {
            "type": "minecraft:condition",
            "if_true": {
              "type": "minecraft:vertical_gradient",
              "random_name": "minecraft:deepslate",
              "true_at_and_below": {
                "absolute": 0
              },
              "false_at_and_above": {
                "absolute": 8
              }
            },
            "then_run": {
              "type": "minecraft:block",
              "result_state": {
                "Name": "minecraft:deepslate",
                "Properties": {
                  "axis": "y"
                }
              }
            }
          }
```


EXAMPLE FILE HOW IT LOOK IN THE FULL CODE:
```json
{
  "type": "beyond_earth:glacio",
  "generator": {
    "type": "beyond_earth:planet_noise",
    "seed": 0,
    "settings": {
      "sea_level": 63,
      "disable_mob_generation": true,
      "noise_caves_enabled": true,
      "noodle_caves_enabled": true,
      "aquifers_enabled": false,
      "ore_veins_enabled": false,
      "legacy_random_source": false,
      "default_block": {
        "Name": "minecraft:stone"
      },
      "default_fluid": {
        "Name": "minecraft:air"
      },
      "noise": {
        "min_y": -64,
        "height": 384,
        "size_horizontal": 1,
        "size_vertical": 2,
        "island_noise_override": false,
        "amplified": false,
        "large_biomes": false,
        "sampling": {
          "xz_scale": 1,
          "y_scale": 1,
          "xz_factor": 80,
          "y_factor": 90
        },
        "bottom_slide": {
          "target": -30,
          "size": 0,
          "offset": 0
        },
        "top_slide": {
          "target": -10,
          "size": 3,
          "offset": 0
        },
        "terrain_shaper": {
          "offset": 0.3,
          "factor": 4,
          "jaggedness": 0
        }
      },
      "surface_rule": {
        "type": "minecraft:sequence",
        "sequence": [
          {
            "type": "minecraft:condition",
            "if_true": {
              "type": "minecraft:vertical_gradient",
              "random_name": "minecraft:bedrock_floor",
              "true_at_and_below": {
                "above_bottom": 0
              },
              "false_at_and_above": {
                "above_bottom": 5
              }
            },
            "then_run": {
              "type": "minecraft:block",
              "result_state": {
                "Name": "minecraft:bedrock"
              }
            }
          },

          {
            "type": "minecraft:condition",
            "if_true": {
              "type": "minecraft:biome",
              "biome_is": [
                "beyond_earth:glacio",
                "beyond_earth:glacio_ice_spikes"
              ]
            },
            "then_run": {
              "type": "minecraft:condition",
              "if_true": {
                "type": "minecraft:y_above",
                "anchor": {
                  "absolute": 87
                },
                "surface_depth_multiplier": 2,
                "add_stone_depth": false
              },
              "then_run": {
                "type": "minecraft:condition",
                "if_true": {
                  "type": "minecraft:water",
                  "offset": -2,
                  "surface_depth_multiplier": 0,
                  "add_stone_depth": false
                },
                "then_run": {
                  "type": "minecraft:sequence",
                  "sequence": [
                    {
                      "type": "minecraft:condition",
                      "if_true": {
                        "type": "minecraft:stone_depth",
                        "offset": 1,
                        "surface_type": "floor",
                        "add_surface_depth": false,
                        "add_surface_secondary_depth": false
                      },
                      "then_run": {
                        "type": "minecraft:block",
                        "result_state": {
                          "Name": "minecraft:snow_block"
                        }
                      }
                    },
                    {
                      "type": "minecraft:block",
                      "result_state": {
                        "Name": "minecraft:packed_ice"
                      }
                    }
                  ]
                }
              }
            }
          },

          {
            "type": "minecraft:condition",
            "if_true": {
              "type": "minecraft:vertical_gradient",
              "random_name": "minecraft:deepslate",
              "true_at_and_below": {
                "absolute": 0
              },
              "false_at_and_above": {
                "absolute": 8
              }
            },
            "then_run": {
              "type": "minecraft:block",
              "result_state": {
                "Name": "minecraft:deepslate",
                "Properties": {
                  "axis": "y"
                }
              }
            }
          }
        ]
      },
      "structures": {
        "structures": {}
      }
    },
    "biome_source": {
      "type": "minecraft:multi_noise",
      "biomes": [
        {
          "biome": "beyond_earth:glacio",
          "parameters": {
            "temperature": 1,
            "humidity": -1,
            "continentalness": 0,
            "erosion": 0,
            "weirdness": -0.5,
            "depth": 0,
            "offset": 0
          }
        },
        {
          "biome": "beyond_earth:glacio_ice_spikes",
          "parameters": {
            "temperature": -0.5,
            "humidity": 0,
            "continentalness": 0,
            "erosion": 0,
            "weirdness": -1.5,
            "depth": 0,
            "offset": 0
          }
        }
      ]
    }
  }
}
```

PICTURE of the Dimension:
![2022-01-03_12 07 13](https://user-images.githubusercontent.com/65916181/147923880-f2245532-cb4d-4634-b033-82cb4404a8a7.png)

