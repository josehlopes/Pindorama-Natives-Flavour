the_tamoio_confederation = {
    slot = 1
    generic = no
    ai = no

    potential = {
        tag = TMO
        NOT = { map_setup = map_setup_random }
    }

    tmo_union_of_tribes = {
        icon = native_royal_marriage
        slot = 1
        position = 1
        required_missions = {} #None
        trigger = {
            num_of_allies = 2
        }
        
        effect = {
            add_country_modifier = {
                name = "influential_diplomacy"
                duration = 9125 #25 years
            }
                
            define_advisor = {
                type = diplomat
                skill = 1
                culture = ROOT
                religion = ROOT
                cost_multiplier = 0.0
            }
        }
    }
    
    tmo_strengthen_the_confederation = {
        icon = mission_iroquois_warriors
        required_missions = { tmo_union_of_tribes }
        slot = 1
        position = 2

        trigger = {
            is_federation_leader = yes
            federation_size = 3
        }
        
        effect = {
            add_country_modifier = {
                name = "tupi_military_morale_of_the_confederation"
                duration = 18250 #50 years
            }
            add_tribal_allegiance = 10
            add_federal_cohesion = 100
        }
    }
    
    tmo_enemy_of_my_enemy = {
        icon = mission_alliances
        slot = 2
        position = 2
        required_missions = { tmo_union_of_tribes }
        
        trigger = {
            europe = { has_discovered = ROOT }
            exists = FRA
            FRA = {
                has_opinion = {
                    who = TMO
                    value = 80
                }
            }
            OR = {
                brazil_region = {
                    any_country = {
                        is_colonial_nation = yes
                    }
                }
                any_neighbor_country = {
                    capital_scope = { continent = europe }
                    OR = { technology_group = western }
                }
            }
        }
        
        effect = {
            country_event = { id = NF_Tamoio_Events.1 days = 1 }
        }
    }

}
