TMO_missions_1 = {
	slot = 1
	generic = no
	ai = yes
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
	
	ANU_purge_the_yamato = {
		icon = mission_asian_city
		position = 4
		required_missions = { ANU_conquer_northern_japan }
		trigger = {
			num_of_owned_provinces_with = {
				value = 10
				region = japan_region
				culture = ainu
			}
		}
		effect = {
			add_country_modifier = {
				name = ANU_spreading_the_culture
				duration = -1
			}
		}
	}
}

TMO_missions_2 = {
	slot = 2
	generic = no
	ai = yes
	potential = {
		tag = TMO
		NOT = { map_setup = map_setup_random }
	}
	
	tmo_settle_tribe = {
		icon = mission_native_dev_capital
		position = 2
		required_missions = { }
		
		trigger = {
			government_reform_progress = 100
		}
		
		effect = {
			add_government_reform = native_settle_down_reform
		}
	}
	
	ANU_conquer_northern_japan = {
		icon = mission_invade_island
		position = 3
		required_missions = { ANU_expel_the_japanese }
		provinces_to_highlight = {
			area = thohoku_area
			NOT = { country_or_non_sovereign_subject_holds = ROOT }
		}
		trigger = {
			thohoku_area = {
				type = all
				country_or_non_sovereign_subject_holds = ROOT
			}
		}
		effect = {
			thohoku_area = {
				add_nationalism = -10
				add_province_modifier = {
					name = ANU_conversion_buff
					duration = -1
				}
			}
			japan_region = {
				limit = {
					NOT = { owned_by = ROOT }
					NOT = { is_core = ROOT }
				}
				add_permanent_claim = ROOT
			}
		}
	}
}

TMO_missions_3 = {
	slot = 3
	generic = no
	ai = yes
	potential = {
		tag = TMO
		NOT = { map_setup = map_setup_random }
	}
	
	tmo_tamoio_confederation = {
		icon = mission_iroquois_warriors
		required_missions = { tmo_union_of_tribes }
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
	
	ANU_unite_the_isles = {
		icon = mission_japanese_samurai
		position = 4
		required_missions = { ANU_conquer_northern_japan }
		trigger = {
			num_of_provinces_owned_or_owned_by_non_sovereign_subjects_with = {
				value = 40
				region = japan_region
			}
		}
		effect = {
			add_country_modifier = {
				name = ANU_the_empire_of_the_rising_sun
				duration = -1
			}
		}
	}
}

TMO_missions_4 = {
	slot = 4
	generic = no
	ai = yes
	potential = {
		tag = TMO
		NOT = { map_setup = map_setup_random }
	}
	
	tmo_strengthen_the_confederation = {
		icon = mission_iroquois_warriors
		required_missions = { tmo_union_of_tribes tmo_tamoio_confederation}
		position = 2
		
		trigger = {
			federation_size = 5
		}
		
		effect = {
			add_country_modifier = {
				name = "tupi_military_morale_of_the_confederation"
				duration = 18250 #50 years
			}
		}
	}
	
	tmo_enemy_of_my_enemy = {
		icon = mission_alliances
		position = 3
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

ANU_missions_5 = {
	slot = 5
	generic = no
	ai = yes
	potential = {
		tag = ANU
		OR = {
			AND = {
				NOT = { has_reform = indep_daimyo }
				NOT = { has_reform = daimyo }
				NOT = { has_reform = shogunate }
			}
			has_country_flag = use_missions_expanded_missions_instead_of_paradox
		}
	}
	has_country_shield = yes
	
	ANU_improve_seafaring = {
		icon = mission_sea_battles
		position = 1
		required_missions = { }
		trigger = {
			OR = {
				num_of_heavy_ship = 1
				num_of_galley = 5
			}
		}
		effect = {
			add_navy_tradition = 5
			1033 = {
				if = {
					limit = {
						is_city = no
						OR = {
							is_empty = yes
							owned_by = ROOT
						}
					}
					add_siberian_construction = 50
				}
			}
		}
	}
	
	ANU_take_over_kamchatka = {
		icon = mission_rb_settle_the_north
		position = 3
		required_missions = { ANU_sakhalin_influences }
		provinces_to_highlight = {
			area = kamchatka_area
			NOT = { country_or_non_sovereign_subject_holds = ROOT }
		}
		trigger = {
			kamchatka_area = {
				country_or_non_sovereign_subject_holds = ROOT
			}
		}
		effect = {
			add_adm_power = 50
			add_dip_power = 50
			add_mil_power = 50
		}
	}
}