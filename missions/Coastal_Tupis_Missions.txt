tupi_military_missions = {
    
    slot = 1
    generic = no
    ai = yes
    
    potential = {
        is_a_coastal_tupi_tribe = yes
    }
    
    tupi_costal_warriors = {
        
        icon = mission_native_build_army_mission
        position = 1
        required_missions = { }
        
        trigger = {
            manpower_percentage = 0.8
            army_size_percentage = 0.8
            num_of_generals = 1
        }
        
        effect = {
            add_army_tradition = 15
            attack_bonus_in_capital_terrain = 1
        }
        
    }
    
    tupi_expand_the_tribe = {
        icon = mission_native_build_army_mission
        position = 2
        required_missions = { tupi_costal_warriors }
        trigger = {
            army_size_percentage = 1
            capital_scope = {
                base_manpower = 6
            }
        }
        
        effect = {
            add_country_modifier = {
                name = "thriving_arms_industry"
                duration = 9125 #25 years
            }
            custom_tooltip = claim_neighbor_province
            hidden_effect = {
                every_owned_province = {
                    every_neighbor_province = {
                        limit = {
                            NOT = { owned_by = ROOT }
                            NOT = { is_permanent_claim = ROOT }
                            NOT = { is_core = ROOT }
                        }
                        add_claim = ROOT
                    }
                }
            }
        }
    }
    
    tupi_remove_europeans = {
        icon = mission_settlers_north_america
        position = 3
        required_missions = { tupi_expand_the_tribe }
        trigger = {
            OR = {
                is_tribal = no
                has_reform = steppe_horde
            }
            NOT = {
                government = native
            }
            has_institution = feudalism
            custom_trigger_tooltip = {
                tooltip = new_world_remove_euro_toolip
                capital_scope = {
                    region_for_scope_province = {
                        type = all
                        NOT = {
                            owner = {
                                technology_group = western
                            }
                        }
                    }
                }
            }
        }
        effect = {
            add_mil_power = 200
            add_country_modifier = {
                name = "military_victory"
                duration = 7300
            }
            custom_tooltip = perma_claim_neighbor_area
            hidden_effect = {
                every_owned_province = {
                    every_neighbor_province = {
                        area = {
                            limit = {
                                NOT = { owned_by = ROOT }
                                NOT = { is_permanent_claim = ROOT    }
                                NOT = { is_core = ROOT    }
                            }
                            add_permanent_claim = ROOT
                        }
                    }
                }
            }
        }
    }
}