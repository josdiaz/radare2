BIN=radare2
BINDEPS=r_core r_parse r_search r_cons r_lib r_config
BINDEPS+=r_bin r_debug r_anal r_diff r_reg r_bp r_io r_cmd r_fs
BINDEPS+=r_sign r_lang r_asm r_syscall r_db r_hash
BINDEPS+=r_magic r_socket r_flags r_util r_egg

include ../rules.mk

sign:
	ldid -Sradare2.xml radare2

osxsign:
	${CC} radare2.o ${CFLAGS} ${LDFLAGS} -sectcreate __TEXT __info_plist ./Info.plist -o radare2 -framework Security -framework CoreFoundation
	codesign -dvvv -s radare2 ./radare2
	sudo chown root:procmod radare2
	sudo chmod g+s radare2

ifeq ($(OSTYPE),android)
LDFLAGS+=${DL_LIBS} -lm
endif
ifeq ($(OSTYPE),qnx)
LDFLAGS+=-lsocket
endif
