# General

## login

***

### 地址: /api/v1/agent/login

***

### 角色:

- agent

***

### 权限:

- read

***

### 参数

| 参数名 | 类型 | 是否必须 | 说明 |
| :-: | :-: | :-: | :-: |
| username | string | true | 当前代理用户名 |
| password | string | true | sha256 |
| role | string | true | 当前角色，example: "admin" \|\| "agent" |

***

### 响应说明

- data
    - token
    - tokenExpired

***

### 响应举例

    {
        token: "",
        tokenExpired:"2018-09-19 18:55:56"
    }

***

# agent

## getAgents

***

### 地址: /api/v1/agent/getAgents

***

### 角色:

- admin 任意
- agent 仅操作 parent_agent_fid 为自己的

***

### 权限:

- read

***

### 参数

| 参数名 | 类型 | 是否必须 | 说明 |
| :-: | :-: | :-: | :-: |
| token | string | true | 当前代理持有的token |
| username | string | true | 当前代理用户名 |
| role | string | true | 当前角色，example: "admin" \|\| "agent" \|\| "user" |
| attributes? | object | false | 需要获取代理的key-value 属性对，example:{level:3,parent_agent_fid:"agent/12345"} |
| offset | string | true | 起始位置 |
| count | string | true | 总数 |

***

### 响应说明

- data
    - agents
    - totalCount
    - pageInfo
        - endCursor
        - hasNextPage

***

### 响应举例

    {
        agents: [
            {
                _id:"",
                username:"",
                password:"",
                name:"",
                agent_name:"",
                sex:"",
                age:"",
                wx_open_id:"",
                wx_union_id:"",
                cellphone:"",
                telephone:"",
                email:""
            },
            {
                _id:"",
                username:"",
                password:"",
                name:"",
                agent_name:"",
                sex:"",
                age:"",
                wx_open_id:"",
                wx_union_id:"",
                cellphone:"",
                telephone:"",
                email:""
            }
        ]
        ,
        totalCount: 200,
        pageInfo:{
            endCursor: 5,
            hasNextPage: true
        }
    }

***

## addAgents

***

### 地址: /api/v1/agent/addAgents

***

### 角色:

- admin 任意
- agent 仅增加 parent_agent_fid 为自己的

***

### 权限:

- edit

***

### 参数

| 参数名 | 类型 | 是否必须 | 说明 |
| :-: | :-: | :-: | :-: |
| token | string | true | 代理持有的token |
| username | string | true | 当前代理用户名 |
| role | string | true | 当前角色，example: "admin" \|\| "agent" \|\| "user" |
| agents | array | true | agent数组 |

***

### 响应说明

- data
    - agents
    - msg

***

### 响应举例

    {
        agents: [
            {
                _id:"",
                username:"",
                password:"",
                name:"",
                agent_name:"",
                sex:"",
                age:"",
                wx_open_id:"",
                wx_union_id:"",
                cellphone:"",
                telephone:"",
                email:""
            },
            {
                _id:"",
                username:"",
                password:"",
                name:"",
                agent_name:"",
                sex:"",
                age:"",
                wx_open_id:"",
                wx_union_id:"",
                cellphone:"",
                telephone:"",
                email:""
            }
        ]
        ,
        msg:{
            error?: Error(),
            api:"addAgents",
            code:"000008",
            content:"addAgents success."
        }
    }

***

## editAgents

***

### 地址: /api/v1/agent/editAgents

***

### 角色:

- admin 任意
- agent 仅操作 parent_agent_fid 为自己的,不允许修改 parent_agent_fid

***

### 权限:

- edit

***

### 参数

| 参数名 | 类型 | 是否必须 | 说明 |
| :-: | :-: | :-: | :-: |
| token | string | true | 代理持有的token |
| username | string | true | 当前代理用户名 |
| role | string | true | 当前角色，example: "admin" \|\| "agent" \|\| "user" |
| agentsQueryAndEdit | array | true | 需要获取代理的key-value 属性对数组，example:\[{queryAttributes:{_id:"agent/12345",username:"wukong"},editAttributes:{level:3,parent_agent_fid:"agent/12345"}}\] |

***

### 响应说明

- data
    - agents
    - msg

***

### 响应举例

    {
        agents: [
            {
                _id:"",
                username:"",
                password:"",
                name:"",
                agent_name:"",
                sex:"",
                age:"",
                wx_open_id:"",
                wx_union_id:"",
                cellphone:"",
                telephone:"",
                email:""
            },
            {
                _id:"",
                username:"",
                password:"",
                name:"",
                agent_name:"",
                sex:"",
                age:"",
                wx_open_id:"",
                wx_union_id:"",
                cellphone:"",
                telephone:"",
                email:""
            }
        ]
        ,
        msg:{
            error?: Error(),
            api:"editAgents",
            code:"000008",
            content:"addAgents success."
        }
    }

***

## deleteAgents

***

### 地址: /api/v1/agent/deleteAgents

***

### 角色:

- admin 任意
- agent 仅操作 parent_agent_fid 为自己的

***

### 权限:

- edit

***

### 参数

| 参数名 | 类型 | 是否必须 | 说明 |
| :-: | :-: | :-: | :-: |
| token | string | true | 当前代理持有的token |
| username | string | true | 当前代理用户名 |
| role | string | true | 当前角色，example: "admin" \|\| "agent" \|\| "user" |
| agents | array | true | 需要获取代理的key-value 属性对，example:\[{_id:"agent/12345",username:"wukong"}\] |

***

### 响应说明

- data
    - agents
    - msg

***

### 响应举例

    {
        agents: [
            {
                _id:"",
                username:"",
                password:"",
                name:"",
                agent_name:"",
                sex:"",
                age:"",
                wx_open_id:"",
                wx_union_id:"",
                cellphone:"",
                telephone:"",
                email:""
            },
            {
                _id:"",
                username:"",
                password:"",
                name:"",
                agent_name:"",
                sex:"",
                age:"",
                wx_open_id:"",
                wx_union_id:"",
                cellphone:"",
                telephone:"",
                email:""
            }
        ]
        ,
        msg:{
            error?: Error(),
            api:"deleteAgents",
            code:"000008",
            content:"deleteAgents success."
        }
    }

***

# device

## getDevices

***

### 地址: /api/v1/device/getDevices

***

### 角色:

- admin 任意
- agent 仅操作 agent_fid 为自己的
- user 仅查看到代理信息

***

### 权限:

- read

***

### 参数

| 参数名 | 类型 | 是否必须 | 说明 |
| :-: | :-: | :-: | :-: |
| token | string | true | 当前代理持有的token |
| username | string | true | 当前代理用户名 |
| role | string | true | 当前角色，example: "admin" \|\| "agent" \|\| "user" |
| attributes? | object | false | 需要获取设备的key-value 属性对，example:{sn_code:"",device_type_fid:""} |
| offset | string | true | 起始位置 |
| count | string | true | 总数 |

***

### 响应说明

- data
    - devices
    - totalCount
    - pageInfo
        - endCursor
        - hasNextPage

***

### 响应举例

    {
        devices: [
            {
                _id:"",
                username:"",
                password:"",
                name:"",
                agent_name:"",
                sex:"",
                age:"",
                wx_open_id:"",
                wx_union_id:"",
                cellphone:"",
                telephone:"",
                email:""
            },
            {
                _id:"",
                username:"",
                password:"",
                name:"",
                agent_name:"",
                sex:"",
                age:"",
                wx_open_id:"",
                wx_union_id:"",
                cellphone:"",
                telephone:"",
                email:""
            }
        ]
        ,
        totalCount: 200,
        pageInfo:{
            endCursor: 5,
            hasNextPage: true
        }
    }

***

## addDevices

***

### 地址: /api/v1/device/addDevices

***

### 角色:

- admin 任意

***

### 权限:

- edit

***

### 参数

| 参数名 | 类型 | 是否必须 | 说明 |
| :-: | :-: | :-: | :-: |
| token | string | true | 代理持有的token |
| username | string | true | 当前代理用户名 |
| role | string | true | 当前角色，example: "admin" \|\| "agent" \|\| "user" |
| devices | array | true | devices数组 |

***

### 响应说明

- data
    - agents
    - msg

***

### 响应举例

    {
        devices: [
            {
                _id:"",
                username:"",
                password:"",
                name:"",
                agent_name:"",
                sex:"",
                age:"",
                wx_open_id:"",
                wx_union_id:"",
                cellphone:"",
                telephone:"",
                email:""
            },
            {
                _id:"",
                username:"",
                password:"",
                name:"",
                agent_name:"",
                sex:"",
                age:"",
                wx_open_id:"",
                wx_union_id:"",
                cellphone:"",
                telephone:"",
                email:""
            }
        ]
        ,
        msg:{
            error?: Error(),
            api:"addDevices",
            code:"000008",
            content:"successful."
        }
    }

***

## editDevices

***

### 地址: /api/v1/device/editDevices

***

### 角色:

- admin 任意
- agent 仅操作 agent_fid 为自己的， agent_fid 仅可修改为自己所属一级代理,不允许修改 sn_code,name,device_type_fid

***

### 权限:

- edit

***

### 参数

| 参数名 | 类型 | 是否必须 | 说明 |
| :-: | :-: | :-: | :-: |
| token | string | true | 代理持有的token |
| username | string | true | 当前代理用户名 |
| role | string | true | 当前角色，example: "admin" \|\| "agent" \|\| "user" |
| deviceQueryAndEdit | array | true | 需要获取和修改设备的key-value 属性对数组，example:\[{queryAttributes:{_id:"device/12345",sn_code:"wukong"},editAttributes:{user_fid:"user/12345",agent_fid:"agent/12345"}}\] |

***

### 响应说明

- data
    - devices
    - msg

***

### 响应举例

    {
        devices: [
            {
                _id:"",
                username:"",
                password:"",
                name:"",
                agent_name:"",
                sex:"",
                age:"",
                wx_open_id:"",
                wx_union_id:"",
                cellphone:"",
                telephone:"",
                email:""
            },
            {
                _id:"",
                username:"",
                password:"",
                name:"",
                agent_name:"",
                sex:"",
                age:"",
                wx_open_id:"",
                wx_union_id:"",
                cellphone:"",
                telephone:"",
                email:""
            }
        ]
        ,
        msg:{
            error?: Error(),
            api:"editDevices",
            code:"000008",
            content:"successful."
        }
    }

***

## deleteDevices

***

### 地址: /api/v1/device/deleteDevices

***

### 角色:

- admin 任意

***

### 权限:

- edit

***

### 参数

| 参数名 | 类型 | 是否必须 | 说明 |
| :-: | :-: | :-: | :-: |
| token | string | true | 当前代理持有的token |
| username | string | true | 当前代理用户名 |
| role | string | true | 当前角色，example: "admin" \|\| "agent" \|\| "user" |
| devices | array | true | 需要删除设备的key-value 属性对，example:\[{_id:"device/12345",sn_code:""}\] |

***

### 响应说明

- data
    - agents
    - msg

***

### 响应举例

    {
        agents: [
            {
                _id:"",
                username:"",
                password:"",
                name:"",
                agent_name:"",
                sex:"",
                age:"",
                wx_open_id:"",
                wx_union_id:"",
                cellphone:"",
                telephone:"",
                email:""
            },
            {
                _id:"",
                username:"",
                password:"",
                name:"",
                agent_name:"",
                sex:"",
                age:"",
                wx_open_id:"",
                wx_union_id:"",
                cellphone:"",
                telephone:"",
                email:""
            }
        ]
        ,
        msg:{
            error?: Error(),
            api:"deleteAgents",
            code:"000008",
            content:"addAgents success."
        }
    }

***


