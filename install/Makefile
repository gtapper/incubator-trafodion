
# @@@ START COPYRIGHT @@@
#
#  Licensed under the Apache License, Version 2.0 (the "License");
#  you may not use this file except in compliance with the License.
#  You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
#  Unless required by applicable law or agreed to in writing, software
#  distributed under the License is distributed on an "AS IS" BASIS,
#  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#  See the License for the specific language governing permissions and
#  limitations under the License.
#
# @@@ END COPYRIGHT @@@
RELEASE_VER ?= $(shell echo $(TRAFODION_VER))
RELEASE_TYPE ?= $(shell echo $(TRAFODION_VER_PROD)| sed -e 's/ /-/g')
INSTALLER_TARNAME = $(shell echo ${RELEASE_TYPE}_installer-${RELEASE_VER}.tar.gz |tr '[A-Z]' '[a-z]')

all: pkg-installer 

pkg-installer: installer/LICENSE installer/NOTICE
	tar czf ${INSTALLER_TARNAME} installer --exclude=tools
	mkdir -p ../distribution
	mv ${INSTALLER_TARNAME} ../distribution

installer/LICENSE: ../licenses/LICENSE-install
	cp -f $? $@

../licenses/LICENSE-install:
	cd $(@D) && $(MAKE) $(@F)

installer/NOTICE: ../NOTICE
	cp -f $? $@

version:
	@echo "$(RELEASE_VER)"

clean:
	rm -f ${INSTALLER_TARNAME} 
