add_library(ctf SHARED
	g_ai.c
	g_chase.c
	g_cmds.c
	g_combat.c
	g_ctf.c
	g_func.c
	g_items.c
	g_main.c
	g_misc.c
	g_monster.c
	g_phys.c
	g_save.c
	g_spawn.c
	g_svcmds.c
	g_target.c
	g_trigger.c
	g_utils.c
	g_weapon.c
	m_move.c
	p_client.c
	p_hud.c
	p_menu.c
	p_trail.c
	p_view.c
	p_weapon.c
	q_shared.c)
set_target_properties(ctf PROPERTIES CLEAN_DIRECT_OUTPUT 1 OUTPUT_NAME "game${ARCH}" PREFIX "")
target_link_libraries(ctf ${LDFLAGS})
