---
title: 发送和处理错误
ms.date: 03/30/2017
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
ms.openlocfilehash: 6796b4daccd88adc3bd006f454ce96ca155fbcb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516121"
---
# <a name="sending-and-handling-faults"></a>发送和处理错误
此示例演示如何使用 <xref:System.ServiceModel.Activities.SendReply> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 消息传递活动来发送和接收预期的和意外的错误。 在此方案中，第一个客户端请求导致已包含在其 <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> 集合中的预期错误。 在最终请求成功之前，接下来的几个客户端请求会导致接收意外错误。  
  
## <a name="to-use-this-sample"></a>使用此示例  
  
1.  打开[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]使用提升的权限，通过右键单击[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]图标并选择**以管理员身份运行**。  
  
2.  打开 Faults.sln 解决方案文件。  
  
3.  要生成解决方案，按 Ctrl+Shift+B。  
  
4.  运行服务项目。  
  
    1.  在**解决方案资源管理器**，右键单击`FaultService`项目，然后选择**设为启动项目**。  
  
    2.  按 Ctrl+F5。  
  
5.  打开的另一个副本[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]使用提升的权限，通过右键单击[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]图标并选择**以管理员身份运行**。  
  
6.  打开 Faults.sln 解决方案文件。  
  
7.  运行客户端项目。  
  
    1.  在**解决方案资源管理器**，右键单击`FaultClient`项目，然后选择**设为启动项目**。  
  
    2.  按 Ctrl+F5。  
  
> [!IMPORTANT]
>  您的计算机上可能已安装这些示例。 在继续操作之前，请先检查以下（默认）目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和针对.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](http://go.microsoft.com/fwlink/?LinkId=150780)下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。 此示例位于以下目录：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`