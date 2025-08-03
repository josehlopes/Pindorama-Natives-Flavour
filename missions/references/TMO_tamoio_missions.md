TMO_missions_1 = {
	slot = 1
	generic = no
	ai = yes
	has_country_shield = yes
	
	potential = {
		tag = TMO
		NOT = { map_setup = map_setup_random }
	}
	
	tmo_settle_tribe = {
		icon = mission_native_dev_capital
		position = 1
		required_missions = { }
		
		trigger = {
			government_reform_progress = 100
		}
		
		effect = {
			add_government_reform = native_settle_down_reform
			colonists = 1
		}
	}
	
	tmo_stabilize_nation = {
		icon = mission_control_unrest
		position = 4
		required_missions = { tmo_modernize_the_tribe }
		trigger = {
			stability = 3
		}
		
		effect = {
			add_prestige = 70
		}
	}
}

TMO_missions_2 = {
	slot = 2
	generic = no
	ai = yes
	has_country_shield = yes
	
	potential = {
		tag = TMO
		NOT = { map_setup = map_setup_random }
	}
	
	tmo_modernize_the_tribe = {
		icon = mission_ne_longhouses
		position = 2
		required_missions = { tmo_union_of_tribes tmo_settle_tribe }
		
		trigger = {
			adm_tech = 5
		}
		
		effect = {
			TMO = {
				embrace_institution = feudalism
			}
		}
	}
	
	tmo_tamoio_economic_boom = {
		icon = mission_african_gold
		position = 3
		required_missions = { tmo_modernize_the_tribe }
		
		trigger = {
			num_of_development_provinces = {
				development = 10
				amount = 3
			}
		}
		
		effect = {
			add_country_modifier = {
				name = tupi_coastal_power
				duration = 18250 #50 Years
			}
		}
	}
}

TMO_missions_3 = {
	slot = 3
	generic = no
	ai = yes
	has_country_shield = yes
	
	potential = {
		tag = TMO
		NOT = { map_setup = map_setup_random }
	}
	
	tmo_union_of_tribes = {
		icon = native_royal_marriage
		position = 1
		required_missions = { } #None
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
	
	tmo_create_tamoio_nation = {
		icon = mission_unite_home_region
		position = 4
		required_missions = { tmo_tamoio_economic_boom }
		
		trigger = {
			army_size_percentage = 100
		}
		
		effect = {
			rio_de_janeiro_area = {
				limit = {
					NOT = { owned_by = ROOT }
					NOT = { is_permanent_claim = ROOT }
				}
				add_permanent_claim = ROOT
			}
			sao_paolo_area = {
				limit = {
					NOT = { owned_by = ROOT }
					NOT = { is_permanent_claim = ROOT }
				}
				add_permanent_claim = ROOT
			}
			minas_gerais_area = {
				limit = {
					NOT = { owned_by = ROOT }
					NOT = { is_permanent_claim = ROOT }
				}
				add_permanent_claim = ROOT
			}
		}
	}
}

TMO_missions_4 = {
	slot = 4
	generic = no
	ai = yes
	has_country_shield = yes
	
	potential = {
		tag = TMO
		NOT = { map_setup = map_setup_random }
	}
	
	tmo_enemy_of_my_enemy = {
		icon = mission_alliances
		position = 2
		required_missions = { tmo_union_of_tribes tmo_tamoio_confederation }
		
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
	
	tmo_gain_knowledge = { #TODO: CRIAR NOVA MISSÃO
		icon = mission_sio_european_trade
		position = 3
		required_missions = { tmo_enemy_of_my_enemy }
		trigger = {
			adm_tech = 5
		}
		
		effect = {
			TMO = {
				effect = { embrace_institution = feudalism }
		}
	}
}

TMO_missions_5 = {
	slot = 5
	generic = no
	ai = yes
	has_country_shield = yes
	
	potential = {
		tag = TMO
		NOT = { map_setup = map_setup_random }
	}
	
	tmo_tamoio_confederation = {
		icon = mission_iroquois_warriors
		required_missions = { }
		position = 1
		
		trigger = {
			is_federation_leader = yes
		}
		
		effect = {
			add_country_modifier = {
				name = "tupi_military_morale_of_the_confederation"
				duration = 18250 #50 years
			}
		}
	}
	
	tmo_a_new_religon = {
		icon = mission_european_church
		position = 3
		required_missions = { tmo_enemy_of_my_enemy }
		trigger = {
			any_country = {
				religion = catholic
				has_opinion = {
					who = ROOT
					value = 80
				}
			}
		}
		effect = {
			country_event = { id = NF_Tamoio_Events.2 }
		}
	}
}