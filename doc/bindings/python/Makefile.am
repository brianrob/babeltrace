SPHINX_SOURCE_DIR = $(srcdir)/source
SPHINX_BUILD_DIR = build
SPHINX_BUILD_HTML_DIR = $(SPHINX_BUILD_DIR)/html
SPHINX_BUILD_DIRHTML_DIR = $(SPHINX_BUILD_DIR)/dirhtml
SPHINX_HTML_TARGET = $(SPHINX_BUILD_HTML_DIR)/index.html
SPHINX_DIRHTML_TARGET = $(SPHINX_BUILD_DIRHTML_DIR)/index.html

EXTRA_DIST = $(srcdir)/source $(srcdir)/sphinx-build.py

all-local: $(SPHINX_HTML_TARGET) $(SPHINX_DIRHTML_TARGET)

PYTHON_BABELTRACE_BUILD_LIB_DIR = $(abs_top_builddir)/bindings/python/babeltrace/build/build_lib
PYTHON_BT2_BUILD_LIB_DIR = $(abs_top_builddir)/bindings/python/bt2/build/build_lib
PP = $(PYTHON_BABELTRACE_BUILD_LIB_DIR):$(PYTHON_BT2_BUILD_LIB_DIR)
LLP = $(abs_top_builddir)/lib/.libs
LOCAL_SPHINXBUILD = PYTHONPATH="$(PP)" LD_LIBRARY_PATH="$(LLP)" $(PYTHON) $(srcdir)/sphinx-build.py
SPHINX_SRC = $(wildcard $(SPHINX_SOURCE_DIR)/*.rst)

$(SPHINX_HTML_TARGET): $(SPHINX_SRC)
	$(LOCAL_SPHINXBUILD) -b html -E $(SPHINX_SOURCE_DIR) $(SPHINX_BUILD_HTML_DIR)

$(SPHINX_DIRHTML_TARGET): $(SPHINX_SRC)
	$(LOCAL_SPHINXBUILD) -b dirhtml -E $(SPHINX_SOURCE_DIR) $(SPHINX_BUILD_DIRHTML_DIR)

clean-local:
	rm -rf $(SPHINX_BUILD_DIR)
