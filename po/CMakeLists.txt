# Translated languages.
SET(SUPPORTED_TRANSLATION zh_CN zh_TW)
INCLUDE(ManageTranslation)

SET(SOURCES_I18N ../src/IBusChewingEngine.gob
  ../src/IBusChewingEngine-input-events.c ../src/IBusChewingEngine-def.c ../src/main.c)

USE_GETTEXT(ALL SRCS ${SOURCES_I18N} LOCALES ${SUPPORTED_TRANSLATION}
    XGETTEXT_OPTIONS ${XGETTEXT_OPTIONS_C})

IF(EXISTS $ENV{HOME}/.config/zanata.ini)
    SET(ZANATA_SERVER "https://translate.zanata.org" CACHE STRING "ZANATA Server URL")
    USE_ZANATA("${ZANATA_SERVER}")
ENDIF(EXISTS $ENV{HOME}/.config/zanata.ini)
