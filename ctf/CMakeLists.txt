if(${SIZEOF_VOID_PTR} MATCHES "^4$")
	set(ARCH i386)
else(${SIZEOF_VOID_PTR} MATCHES "^4$")
	set(ARCH x86_64)
endif(${SIZEOF_VOID_PTR} MATCHES "^4$")

set(BASE_CFLAGS "")

set(RELEASE_CFLAGS "${BASE_CFLAGS} -m486 -O6 -ffast-math -funroll-loops
	-fomit-frame-pointer -fexpensive-optimizations -malign-loops=2
	-malign-jumps=2 -malign-functions=2")

set(DEBUG_CFLAGS "${BASE_CFLAGS} -g")
set(LDFLAGS -ldl -lm)

set(CTF_OBJS
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
	q_shared.c
)

add_library(ctf SHARED ${CTF_OBJS})
set_target_properties(ctf PROPERTIES CLEAN_DIRECT_OUTPUT 1 OUTPUT_NAME "game${ARCH}")
set_target_properties(ctf PROPERTIES PREFIX "")
set_target_properties(ctf PROPERTIES COMPILE_FLAGS ${DEBUG_CFLAGS})
target_link_libraries(ctf ${LDFLAGS})
