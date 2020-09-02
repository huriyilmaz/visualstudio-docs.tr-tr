---
title: 'Hata: Transact-SQL yürütmesi hata ayıklama olmadan sonlandırıldı | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 7a4d4999-3973-4339-ba6a-f0d19bcb1d4a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cdfcaa42c55f87711b0889c6a67d1a4799b84fed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681072"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Hata: Transact-SQL yürütmesi hata ayıklaması yapılmadan sonlandı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu hata, bir Transact-SQL veya SQLCLR yordamını hata ayıklamaya çalışırken ve hata ayıklayıcı SQL Server hata ayıklama iletilerini almadığında oluşur.  
  
 Bunun nedeni ağ sorunlarından veya SQL Server sorunlarından kaynaklanabilir, ancak en olası nedeni bir izin sorunudur.  
  
 Dahil olmak üzere iki hesap vardır:  
  
- Uygulama hesabı, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] olarak çalışan kullanıcı hesabıdır.  
  
- Bağlantı hesabı, SQL Server bağlantısını yapmak için kullanılan kimliktir. Bu, bağlantı SQL kimlik doğrulaması kullanıyor gibi, Visual Studio 'Nun çalıştırdığı kimlikle aynı değildir.  
  
  SQL hata ayıklaması, uygulama hesabının bağlantı hesabıyla eşleşmesi veya sysadmin olması gerekir.  
  
  Sa gibi bir SQL oturum açma kullanıyorsanız, uygulama hesabının bir sysadmin olarak SQL Server kurulması gerekir. Varsayılan olarak, SQL Server makinesinde çalışan yöneticiler SQL Server sysadmins ' dir.  
  
  Bu hatayı düzeltmek için şunları yapmanız gerekebilir:  
  
- İzin ayarlarınızı doğrulayın. Daha fazla bilgi için bkz. [nasıl yapılır: hata ayıklama için SQL Server Izinleri ayarlama](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
- Doğru ayarlandıysa SQL hata ayıklamanın bulunduğundan emin olun.  
  
- Ağınız veya veritabanı yöneticinizle görüşün.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL hata ayıklamayı ayarlama](https://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [Nasıl yapılır: hata ayıklama için SQL Server Izinleri ayarlama](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Hata ayıklayıcı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)   
 [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
