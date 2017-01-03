#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.61])
AC_INIT([acme-utils], [0.0.1], [s.knoblich@axsentis.de])
AC_CONFIG_SRCDIR([acme-setup-cert.in])
AC_CONFIG_MACRO_DIR([m4])

# override default
AS_IF([test "x${sysconfdir}" = "x\${prefix}/etc"],
	[AC_SUBST([sysconfdir], ["\${prefix}/etc/acme-utils"])]
)

AC_ARG_WITH([certdir],
	[AS_HELP_STRING([--with-certdir@<:@=DIR@:>@], [Location of generated certificates])],
	[certdir="${withval}"],
	[certdir="${sysconfdir}"]
)
AC_SUBST([certdir])

AC_ARG_WITH([challengedir],
	[AS_HELP_STRING([--with-challengedir@<:@=DIR@:>@], [Location of ACME challenges])],
	[challengedir="${withval}"],
	[challengedir="\${prefix}/var/www/acme-challenges"]
)
AC_SUBST([challengedir])

AM_INIT_AUTOMAKE

# Checks for programs.
AC_PATH_PROG([WGET], [wget])
AS_IF([test "x${WGET}" = "x"], [AC_MSG_ERROR([wget not found])])

AC_PATH_PROG([OPENSSL], [openssl])
AS_IF([test "x${OPENSSL}" = "x"], [AC_MSG_ERROR([openssl not found])])

AC_PATH_PROG([PYTHON], [python])
AS_IF([test "x${PYTHON}" = "x"], [AC_MSG_ERROR([python not found])])

AC_PATH_PROG([PWGEN], [pwgen])
AS_IF([test "x${PWGEN}" = "x"], [AC_MSG_ERROR([pwgen not found])])

AC_PATH_PROG([DIG], [dig])
AS_IF([test "x${DIG}" = "x"], [AC_MSG_ERROR([dig not found])])

AC_PATH_PROG([SETFACL], [setfacl])
AS_IF([test "x${SETFACL}" = "x"], [AC_MSG_ERROR([setfacl not found])])

AC_PATH_PROG([SU], [su])
AS_IF([test "x${SU}" = "x"], [AC_MSG_ERROR([su not found])])

# Generate output files
AC_CONFIG_FILES([Makefile])
AC_OUTPUT

AC_MSG_RESULT([
**************** configuration summary *******************

  acme_dir............. ${sysconfdir}
  cert_dir............. ${certdir}
  challenge_dir........ ${challengedir}

*********************************************************
])
