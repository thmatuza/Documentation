
---
title: RTM Limitations
description: 
platform: CPP
updatedAt: Wed Oct 09 2019 03:25:23 GMT+0800 (CST)
---
# RTM Limitations

This page provides a brief overview of the limitations of the Agora RTM SDK for Android, including the maximum method call frequencies, maximum string length, unicode support and more.


## Maximum Call Frequency

| Function                                                    | Method                                                       | Maximum Call Frequency                 |
| ----------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------ |
| Log in the RTM system                                | [login](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_rtm_service.html#a2433a0babbed76ab87084d131227346b) | Two queries per second         |
| Join a channel<sup>1</sup> | [join](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_channel.html#a6a54cdd8e5db526514e0ca84aa9cba4c) | 50 queries every three seconds |
| Send messages | <li>[sendMessageToPeer](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_rtm_service.html#afec5391fa9c4ec2bfe9ac4e684705600)<li> [sendMessageToPeer](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_rtm_service.html#a08c1b3d444af5a2778ede48e4c677a52) <li> And [sendMessage](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_channel.html#a4ae01f44d49f334f7c2950d95f327d30) taken together | 60 queries per second          |
| Retrieve a member list of the channel          | [getMembers](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_channel.html#a3f9c943059ac48a568c81798da38c3cb) | Five queries every two seconds |
| Renew the token| [renewToken](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_rtm_service.html#a2c33be67bfec02d69041f1e8978f4559) | Two queries per second |
| Query the online status of the specified user(s) | [queryPeersOnlineStatus](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_rtm_service.html#a3add0055c4455dc8d04bfc37edfd8e94) | Ten queries every five seconds. |
| Set user attributes                               | <li>[setLocalUserAttributes](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_rtm_service.html#a86dcbfc38c665be8565f06c534338d33)<li>[addOrUpdateLocalUserAttributes](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_rtm_service.html#a0a63923bd1e81e60d6ca54213a329747)<li>[deleteLocalUserAttributesByKeys](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_rtm_service.html#acb669f6c4c28e08cdf889df11e1ddeb3)<li>And [clearLocalUserAttributes](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_rtm_service.html#acc5eee875f4166fe455cde7aff1ad738) taken together | 10 queries every five seconds   |
| Get user attributes                               | <li>[getUserAttributes](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_rtm_service.html#a14cac887f9adb390621dd0427092a65b)<li> And [getUserAttributesByKeys](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_rtm_service.html#af011235917c291df5581f92afa35532f) taken together | 40 queries every five seconds   |
| Set channel attributes | <li>[setChannelAttributes](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_rtm_service.html#aa229a7207062b510799166c1239412fa)<li>[addOrUpdateChannelAttributes](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_rtm_service.html#ae4068ff21c8e20e8eeb45ba21959c368)<li>[deleteChannelAttributesByKeys](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_rtm_service.html#a1a448f33be57b31f9952822426e5c4bd)<li>And [clearChannelAttributes](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_rtm_service.html#aff6cff676e3fc3150ef5f27845c9a3d3) taken together | 10 queries every five seconds         |
| Get channel attributes | <li>[getChannelAttributes](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_rtm_service.html#a3dc8409ed82d8f95a0839d5e9e7da564)<li> And [getChannelAttributesByKeys](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_rtm_service.html#ac97f24f9d78e885e494a22be95db8d33) taken together | 10 queries every five seconds          |

> <sup>1</sup> The maximum call frequency limit for joining the same channel is two queries every five seconds. 

## String Length

- The maximum length of a peer-to-peer or channel message is 32 KB. See [IMessage.setText](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_message.html#a2e93098d5a3819e9d4cf8d42641474ae).
- The maximum length of the content in a call invitation is 8 KB. See [ILocalCallInvitation.setContent](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_local_call_invitation.html#aaf4b356b7602cad2bdb998250617c920).
- The maximum length of the response in a call invitation is 8 KB. See [IRemoteCallInvitation.setResponse](https://docs.agora.io/en/Real-time-Messaging/API%20Reference/RTM_cpp/classagora_1_1rtm_1_1_i_remote_call_invitation.html#a77c8a0902f9dce36525a66575a6ae8a5).

## Unicode support 

Supports channel and peer-to-peer messages, invitation content, and invitation response in UTF-8 only. 


## Miscellaneous 

- Notifications of a member joining or leaving the channel are automatically disabled when the number of channel members exceeds 512. If you have special requirements, contact sales-us@agora.io.
- The current version supports querying the online status of a maximum of 256 users.
- Attribute settings in one user attribute operation should not exceed 16 KB in size; attribute settings in one channel attribute operation should not exceed 32 KB in size; each attribute (key/value pair) should not excced 8 KB in size; the number of key/value pairs you set in one attribute operation should not exceed 32. 