[[Index]] 
```

#!/usr/bin/python3


from __future__ import (absolute_import, division, print_function)
__metaclass__ = type
from ansible.module_utils.basic import AnsibleModule


#example of a few local functions, to calculate area or volume
#you can have your business logic here in form of functions

def get_area(length, breath):
  return length * breath

def get_volume(length, breath, height):
  return length * breath * height

#
# This is the main function body 
#
def main():
    # Define the args required by the module
    # update the aruments as per your requirements
    module_args = dict(
        length=dict(type='int', required=True),
        breath=dict(type='int', required=True),
        height=dict(type='int', required=True),
        action=dict(type='str', required=True),
        radius=dict(type='str', required=False),
    )
    #AnsibleModule class is imported from ansible.module_utils.basic
    # following is the allowed args to AnsibleModule
    # classansible.module_utils.basic.AnsibleModule(argument_spec, bypass_checks=False, no_log=False, mutually_exclusive=None, required_together=None, required_one_of=None, add_file_common_args=False, supports_check_mode=False, required_if=None, required_by=None)
    
    module = AnsibleModule(
        argument_spec=module_args,
        supports_check_mode=True
    )
    #build the default structure of return value, with all empty values
    #we will update this dict called 'result' while returning form the
    #the module with appropriate values

    result = dict(
        msg = '',
        stdout = '',
        stdout_lines = [],
        stderr = '',
        stderr_lines = [],
        rc = 0,
        failed = False,
        changed=False
    )
    
    #validate that the action argument is set to one of the allowed values
    allowed_actions = ['area', 'volume']
    if module.params['action'] not in allowed_actions:
        result['failed'] = True
        result['stderr'] = "Invalid argument supplied to this module"
        module.exit_json(**result)
    action =  module.params['action']
    length =  module.params['length']
    breath =  module.params['breath']
    height =  module.params['height']
    if action == 'area':
        area = get_area(length, breath)
        result['stdout'] = area
        module.exit_json(**result)
    if action == 'volume':
        volume = get_volume(length, breath, height)
        result['stdout'] = volume
        module.exit_json(**result)
    module.exit_json(**result)

if __name__ == '__main__':
    main()

```