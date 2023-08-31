*erro mais recente:*
"
fatal: [localhost]: FAILED! => {

    "msg": "Unable to import community.libvirt.virt due to unindent does not match any outer indentation level"

}
"

*erro de True name:*
"
An exception occurred during task execution. To see the full traceback, use -vvv. The error was: VMNotFound: virtual machine True not found

fatal: [localhost]: FAILED! => {"changed": false, "msg": "virtual machine True not found"}
"

*consertei o erro do name com essa alteração no /usr/lib/python3/dist-packages/ansible_collections/community/libvirt/plugins/modules/virt.py*
**antes**
"
     def core(module):
     
    state = module.params.get('state', None)
    autostart = module.params.get('autostart', None)
    guest = module.params.get('name', None)
    command = module.params.get('command', None)
    uri = module.params.get('uri', None)
    xml = module.params.get('xml', None) 
"
**depois**
"
    def core(module):
    
       state = module.params.get('state', None)
       autostart = module.params.get('autostart', None)
       guest = module.params.get('node2', None)
       command = module.params.get('command', None)
       uri = module.params.get('uri', None)
       xml = module.params.get('xml', None)
"
