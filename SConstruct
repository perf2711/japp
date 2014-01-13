#
# JA++ SCons project file
# written by Raz0r
#
# targets:
#	game
#	cgame
#	ui
#
# options:
#	debug		generate debug information
#	force32		force 32 bit target when on 64 bit machine
#
# example:
#	scons game=1 debug=1 force32=1
#

import platform

plat = platform.system() # Windows or Linux
try:
	bits = int( platform.architecture()[0][:2] ) # 32 or 64
except (ValueError, TypeError ):
	bits = None
arch = None # platform-specific, set manually

print( '\n********************************\n' )
print( 'Configuring build environment...' )
env = Environment()

force32 = int( ARGUMENTS.get( 'force32', 0 ) )
if force32:
	bits = 32

if bits == 32:
	if plat == 'Windows':
		arch = 'x86'
	elif plat == 'Linux':
		arch = 'i386'
elif bits == 64:
	if plat == 'Windows':
		arch = 'x64'
	elif plat == 'Linux':
		arch = 'x86_64'

print( 'Building for ' + plat + ' (' + str(bits) + ' bits, treated as \'' + arch + '\')' )
print( '\n********************************\n' )

files = {}
libs = {}

files['lua'] = [
	'lua/bit.c',
	'lua/lapi.c',
	'lua/lauxlib.c',
	'lua/lbaselib.c',
	'lua/lcode.c',
	'lua/ldblib.c',
	'lua/ldebug.c',
	'lua/ldo.c',
	'lua/ldump.c',
	'lua/lfunc.c',
	'lua/lgc.c',
	'lua/linit.c',
	'lua/liolib.c',
	'lua/llex.c',
	'lua/lmathlib.c',
	'lua/lmem.c',
	'lua/loadlib.c',
	'lua/lobject.c',
	'lua/lopcodes.c',
	'lua/loslib.c',
	'lua/lparser.c',
	'lua/lstate.c',
	'lua/lstring.c',
	'lua/lstrlib.c',
	'lua/ltable.c',
	'lua/ltablib.c',
	'lua/ltm.c',
	'lua/lua.c',
	'lua/lundump.c',
	'lua/lvm.c',
	'lua/lzio.c',
	'lua/print.c' ]

files['udis86'] = [
	'shared/libudis86/decode.c',
	'shared/libudis86/input.c',
	'shared/libudis86/itab.c',
	'shared/libudis86/syn-att.c',
	'shared/libudis86/syn-intel.c',
	'shared/libudis86/syn.c',
	'shared/libudis86/udis86.c' ]

files['game'] = [
	'shared/JAPP/jp_crash.c',
	'shared/JAPP/jp_promode.c',
	'shared/JAPP/jp_tokenparser.c',
	'shared/json/cJSON.c',
	'game/ai_main.c',
	'game/ai_util.c',
	'game/ai_wpnav.c',
	'game/AnimalNPC.c',
	'game/bg_g2_utils.c',
	'game/bg_misc.c',
	'game/bg_panimate.c',
	'game/bg_pmove.c',
	'game/bg_saber.c',
	'game/bg_saberLoad.c',
	'game/bg_saga.c',
	'game/bg_slidemove.c',
	'game/bg_vehicleLoad.c',
	'game/bg_weapons.c',
	'game/FighterNPC.c',
	'game/g_active.c',
	'game/g_admin.c',
	'game/g_arenas.c',
	'game/g_bot.c',
	'game/g_chatFilters.c',
	'game/g_client.c',
	'game/g_clientModification.c',
	'game/g_cmds.c',
	'game/g_combat.c',
	'game/g_exphysics.c',
	'game/g_ICARUScb.c',
	'game/g_items.c',
	'game/g_log.c',
	'game/g_lua.c',
	'game/g_luacvar.c',
	'game/g_luaevent.c',
	'game/g_main.c',
	'game/g_mem.c',
	'game/g_misc.c',
	'game/g_missile.c',
	'game/g_mover.c',
	'game/g_nav.c',
	'game/g_navnew.c',
	'game/g_newmemory.c',
	'game/g_object.c',
	'game/g_playerbans.c',
	'game/g_saga.c',
	'game/g_session.c',
	'game/g_spawn.c',
	'game/g_svcmds.c',
	'game/g_syscalls.c',
	'game/g_target.c',
	'game/g_team.c',
	'game/g_timer.c',
	'game/g_trigger.c',
	'game/g_turret.c',
	'game/g_turret_G2.c',
	'game/g_unlagged.c',
	'game/g_utils.c',
	'game/g_vehicles.c',
	'game/g_vehicleTurret.c',
	'game/g_weapon.c',
	'game/NPC.c',
	'game/NPC_AI_Atst.c',
	'game/NPC_AI_Default.c',
	'game/NPC_AI_Droid.c',
	'game/NPC_AI_GalakMech.c',
	'game/NPC_AI_Grenadier.c',
	'game/NPC_AI_Howler.c',
	'game/NPC_AI_ImperialProbe.c',
	'game/NPC_AI_Interrogator.c',
	'game/NPC_AI_Jedi.c',
	'game/NPC_AI_Mark1.c',
	'game/NPC_AI_Mark2.c',
	'game/NPC_AI_MineMonster.c',
	'game/NPC_AI_Rancor.c',
	'game/NPC_AI_Remote.c',
	'game/NPC_AI_Seeker.c',
	'game/NPC_AI_Sentry.c',
	'game/NPC_AI_Sniper.c',
	'game/NPC_AI_Stormtrooper.c',
	'game/NPC_AI_Utils.c',
	'game/NPC_AI_Wampa.c',
	'game/NPC_behavior.c',
	'game/NPC_combat.c',
	'game/NPC_goal.c',
	'game/NPC_misc.c',
	'game/NPC_move.c',
	'game/NPC_reactions.c',
	'game/NPC_senses.c',
	'game/NPC_sounds.c',
	'game/NPC_spawn.c',
	'game/NPC_stats.c',
	'game/NPC_utils.c',
	'game/q_math.c',
	'game/q_shared.c',
	'game/SpeederNPC.c',
	'game/tri_coll_test.c',
	'game/w_force.c',
	'game/w_saber.c',
	'game/WalkerNPC.c' ] + files['lua'] + files['udis86']

files['cgame'] = [
	'game/AnimalNPC.c',
	'game/bg_g2_utils.c',
	'game/bg_misc.c',
	'game/bg_panimate.c',
	'game/bg_pmove.c',
	'game/bg_saber.c',
	'game/bg_saberLoad.c',
	'game/bg_saga.c',
	'game/bg_slidemove.c',
	'game/bg_vehicleLoad.c',
	'game/bg_weapons.c',
	'game/FighterNPC.c',
	'game/SpeederNPC.c',
	'game/q_math.c',
	'game/q_shared.c',
	'game/WalkerNPC.c',
	'shared/JAPP/jp_promode.c',
	'shared/JAPP/jp_tokenparser.c',
	'shared/json/cJSON.c',
	'ui/ui_shared.c',
	'cgame/cg_chatbox.c',
	'cgame/cg_consolecmds.c',
	'cgame/cg_draw.c',
	'cgame/cg_drawtools.c',
	'cgame/cg_effects.c',
	'cgame/cg_ents.c',
	'cgame/cg_event.c',
	'cgame/cg_info.c',
	'cgame/cg_light.c',
	'cgame/cg_localents.c',
	'cgame/cg_lua.c',
	'cgame/cg_luacvar.c',
	'cgame/cg_luaevent.c',
	'cgame/cg_luaplayer.c',
	'cgame/cg_luaserialiser.c',
	'cgame/cg_luaserver.c',
	'cgame/cg_main.c',
	'cgame/cg_marks.c',
	'cgame/cg_newDraw.c',
	'cgame/cg_newScoreboard.c',
	'cgame/cg_players.c',
	'cgame/cg_playerstate.c',
	'cgame/cg_predict.c',
	'cgame/cg_saga.c',
	'cgame/cg_scoreboard.c',
	'cgame/cg_servercmds.c',
	'cgame/cg_serverModification.c',
	'cgame/cg_smartentities.c',
	'cgame/cg_snapshot.c',
	'cgame/cg_syscalls.c',
	'cgame/cg_teambinds.c',
	'cgame/cg_turret.c',
	'cgame/cg_view.c',
	'cgame/cg_weaponinit.c',
	'cgame/cg_weapons.c',
	'cgame/fx_blaster.c',
	'cgame/fx_bowcaster.c',
	'cgame/fx_bryarpistol.c',
	'cgame/fx_demp2.c',
	'cgame/fx_disruptor.c',
	'cgame/fx_flechette.c',
	'cgame/fx_force.c',
	'cgame/fx_heavyrepeater.c',
	'cgame/fx_rocketlauncher.c' ] + files['lua']

files['ui'] = [
	'shared/JAPP/jp_crash.c',
	'game/bg_misc.c',
	'game/bg_saberLoad.c',
	'game/bg_saga.c',
	'game/bg_vehicleLoad.c',
	'game/bg_weapons.c',
	'game/q_math.c',
	'game/q_shared.c',
	'shared/JAPP/jp_tokenparser.c',
	'shared/json/cJSON.c',
	'ui/ui_atoms.c',
	'ui/ui_cvar.c',
	'ui/ui_force.c',
	'ui/ui_gameinfo.c',
	'ui/ui_main.c',
	'ui/ui_saber.c',
	'ui/ui_shared.c',
	'ui/ui_syscalls.c' ] + files['udis86']

# set up libraries to link with
if plat == 'Linux':
	libs['game'] = [ 'm' ]
	libs['cgame'] = [ 'm' ]
	libs['ui'] = [ 'm' ]
elif plat == 'Windows':
	libs['game'] = []
	libs['cgame'] = []
	libs['ui'] = []

# compiler options
if plat == 'Linux':
	env['CPPDEFINES'] = [ '__GCC__' ]
	env['CCFLAGS'] = [ '-Wall', '-Wextra', '-Wno-missing-braces', '-Wno-missing-field-initializers', '-Wno-sign-compare', '-Wno-unused-parameter' ]
	# this may not be necessary
	if force32:
		env['CCFLAGS'] += [ '-m32' ]
		env['LINKFLAGS'] += [ '-m32' ]
elif plat == 'Windows':
	# assume msvc
	env['CCFLAGS'] = [ '/Gm', '/GS', '/Zc:wchar_t', '/WX-', '/RTC1', '/MDd', '/EHsc', '/nologo', '/W4', '/wd"4100"', '/wd"4127"', '/wd"4996"' ]
	env['LINKFLAGS'] = [ '/SUBSYSTEM:WINDOWS','/MACHINE:'+arch ]
	env['CPPDEFINES'] = [ '_CRT_SECURE_NO_WARNINGS', 'WIN32', '_WINDOWS' ]

# debug / release
if int( ARGUMENTS.get( 'debug', 0 ) ):
	if plat == 'Linux':
		env['CCFLAGS'] += [ '-g3' ]
	elif plat == 'Windows':
		env['CCFLAGS'] += [ '/Zi', '/Od' ]
	env['CPPDEFINES'] += [ '_DEBUG' ]
else:
	if plat == 'Linux':
		env['CCFLAGS'] += [ '-O2' ]
	elif plat == 'Windows':
		env['CCFLAGS'] += [ '/O2' ]
	env['CPPDEFINES'] += [ 'NDEBUG' ]


#################
#    TARGETS    #
#################

# Game
if int(ARGUMENTS.get( 'game', 0 )):
	env['CPPPATH'] = [ '.', './game' ]
	env['CPPDEFINES'] += [ '_GAME', 'JK2AWARDS', 'JPLUA' ]
	env['LIBS'] = libs['game']
	env['LIBPREFIX'] = ''
	env.SharedLibrary( 'jampgame'+arch, files['game'] )

# Client Game
if int(ARGUMENTS.get( 'cgame', 0 )):
	env['CPPPATH'] = [ '.', './cgame', './game' ]
	env['CPPDEFINES'] += [ '_CGAME', 'JK2AWARDS', 'JPLUA' ]
	env['LIBS'] = libs['cgame']
	env['LIBPREFIX'] = ''
	env.SharedLibrary( 'cgame'+arch, files['cgame'] )

# UI
if int(ARGUMENTS.get( 'ui', 0 )):
	env['CPPPATH'] = [ '.', './ui', './game' ]
	env['CPPDEFINES'] += [ '_UI' ]
	env['LIBS'] = libs['ui']
	env['LIBPREFIX'] = ''
	env.SharedLibrary( 'ui'+arch, files['ui'] )
