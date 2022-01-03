# Layer-Tutorial-1.18.1-

BEDROCK LAYER:

`
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
`

TOP LAYER:
`
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
          
`

TOP LAYER WITH SANDSTONE LAYER:
`
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
`

DEEPSLATE LAYER:

`
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
`
