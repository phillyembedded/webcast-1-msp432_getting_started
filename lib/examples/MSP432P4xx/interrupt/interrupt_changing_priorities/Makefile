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
# The default rule, which causes the interrupt_changing_priorities example to be built.
#
all: ${COMPILER}
all: ${COMPILER}/interrupt_changing_priorities.axf

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
# Rules for building the interrupt_changing_priorities example.
#
${COMPILER}/interrupt_changing_priorities.axf: ${COMPILER}/msp432_startup_${COMPILER}.o
${COMPILER}/interrupt_changing_priorities.axf: ${COMPILER}/interrupt_changing_priorities.o
${COMPILER}/interrupt_changing_priorities.axf: ${ROOT}/driverlib/MSP432P4xx/${COMPILER}/msp432p4xx_driverlib.a
${COMPILER}/interrupt_changing_priorities.axf: interrupt_changing_priorities_gcc.ld
SCATTERgcc_interrupt_changing_priorities=interrupt_changing_priorities_gcc.ld
ENTRY_interrupt_changing_priorities=ResetISR
CFLAGSgcc=-DTARGET_IS_MSP432P4XX

#
# Include the automatically generated dependency files.
#
ifneq (${MAKECMDGOALS},clean)
-include ${wildcard ${COMPILER}/*.d} __dummy__
endif
