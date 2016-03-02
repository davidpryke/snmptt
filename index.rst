`snmptt <https://github.com/davidpryke/snmptt/>`_
=================================================

Derived from SNMP Trap Translator v1.4 (r514) at http://www.snmptt.org/

**v1.6beta1 changes:**

* Added helper script ``convert-severity-for-nagios`` to convert severity values from MIB files (such as "OK", "Normal", "WARNING", "CRITICAL") to numeric values 0-3 to be used by Nagios ``submit_check_result script``
* Added ``--preexec=''`` option to snmpttconvertmib to add PREEXEC lines to snmptt config files, for the purpose of using the output of ``convert-severity-for-nagios`` script in the EXEC line as ``$p1`` such as this::

        PREEXEC /usr/sbin/convert-severity-for-nagios $s
        EXEC /usr/bin/sudo -u nagios /usr/local/nagios/libexec/eventhandlers/submit_check_result "$r" "snmp_traps" $p1 "$O: $1 $2 $3 $4 $5"

