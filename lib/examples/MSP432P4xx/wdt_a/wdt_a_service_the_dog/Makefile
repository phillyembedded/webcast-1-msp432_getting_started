#
# Defines the part type that this project uses.
#
PART=__MSP432P401R__

#
# The base directory for MSPWare.
#
ROOT=../../../..

#
# Include the common make definitions.
#
include ../../Makefile.defs

#
# Where to find header files that do not live in the source directory.
#
IPATH=../../../..
IPATH+=../../../../inc/
IPATH+=../../../../inc/CMSIS/
IPATH+=../../../../driverlib/MSP432P4xx

#
# The default rule, which causes the wdt_a_service_the_dog example to be built.
#
all: ${COMPILER}
all: ${COMPILER}/wdt_a_service_the_dog.axf

#
# The rule to clean out all the build products.
#
clean:
	@rm -rf ${COMPILER} ${wildcard *~}

#
# The rule to create the target directory.
#
${COMPILER}:
	@mkdir -p ${COMPILER}

#
# Rules for building the wdt_a_service_the_dog example.
#
${COMPILER}/wdt_a_service_the_dog.axf: ${COMPILER}/msp432_startup_${COMPILER}.o
${COMPILER}/wdt_a_service_the_dog.axf: ${COMPILER}/wdt_a_service_the_dog.o
${COMPILER}/wdt_a_service_the_dog.axf: ${ROOT}/driverlib/MSP432P4xx/${COMPILER}/msp432p4xx_driverlib.a
${COMPILER}/wdt_a_service_the_dog.axf: wdt_a_service_the_dog_gcc.ld
SCATTERgcc_wdt_a_service_the_dog=wdt_a_service_the_dog_gcc.ld
ENTRY_wdt_a_service_the_dog=ResetISR
CFLAGSgcc=-DTARGET_IS_MSP432P4XX

#
# Include the automatically generated dependency files.
#
ifneq (${MAKECMDGOALS},clean)
-include ${wildcard ${COMPILER}/*.d} __dummy__
endif
