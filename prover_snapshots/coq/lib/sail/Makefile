BBV_DIR?=../../../bbv

CORESRC=Sail2_prompt_monad.v  Sail2_prompt.v  Sail2_impl_base.v  Sail2_instr_kinds.v  Sail2_operators_bitlists.v  Sail2_operators_mwords.v  Sail2_operators.v  Sail2_values.v  Sail2_state_monad.v  Sail2_state.v  Sail2_state_lifting.v  Sail2_string.v  Sail2_real.v
PROOFSRC=Sail2_state_monad_lemmas.v Sail2_state_lemmas.v Hoare.v
SRC=$(CORESRC) $(PROOFSRC)

COQ_LIBS = -R . Sail -R "$(BBV_DIR)/theories" bbv

TARGETS=$(SRC:.v=.vo)

.PHONY: all clean *.ide

all: $(TARGETS)
clean:
	rm -f -- $(TARGETS) $(TARGETS:.vo=.glob) $(TARGETS:%.vo=.%.aux) deps

%.vo: %.v
	coqc $(COQ_LIBS) $<

%.ide: %.v
	coqide $(COQ_LIBS) $<

deps: $(SRC)
	coqdep $(COQ_LIBS) $(SRC) > deps

-include deps
