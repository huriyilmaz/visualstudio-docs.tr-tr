---
title: 'Hata: Transact-SQL yürütmesi hata ayıklama olmadan sonlandırıldı | Microsoft Docs'
ms.date: 11/08/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94ced2902becc2e988cde5198eff28911864dcbb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736944"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Hata: Transact-SQL yürütmesi hata ayıklaması yapılmadan sonlandı

Bu hata, bir Transact-SQL veya SQLCLR yordamını hata ayıklamaya çalışırken ve hata ayıklayıcı SQL Server hata ayıklama mesajları almadığında oluşur.

Bu sorun, ağ sorunlarından veya SQL Server sorunlarından kaynaklanıyor olabilir, ancak olası nedeni bir izin sorunudur.

Dahil olmak üzere iki hesap vardır:

- Uygulama hesabı, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çalıştığı kullanıcı hesabıdır.

- Bağlantı hesabı, SQL Server bağlantısını yapmak için kullanılan kimliktir. Bu hesap, bağlantı SQL kimlik doğrulaması kullanıyor gibi, Visual Studio 'Nun çalıştırdığı kimlikle aynı değildir.

  SQL hata ayıklaması, uygulama hesabının bağlantı hesabıyla eşleşmesi veya bir sysadmin olması gerekir.

  Sa gibi bir SQL hesap adı kullanıyorsanız, uygulama hesabının SQL Server sysadmin olarak ayarlanması gerekir. Varsayılan olarak, SQL Server 'ın üzerinde çalıştığı makinedeki Yöneticiler SQL Server sysadmins ' dir.

  Bu hatayı düzeltmek için şunları yapmanız gerekebilir:

  - İzin ayarlarınızı doğrulayın. Daha fazla bilgi için bkz. [nasıl yapılır: hata ayıklama için SQL Server Izinleri ayarlama](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

  - Doğru ayarlandıysa SQL hata ayıklamanın bulunduğundan emin olun.

  - Ağınız veya veritabanı yöneticinizle görüşün.

## <a name="see-also"></a>Ayrıca bkz.

- [SQL hata ayıklamayı ayarlama](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Nasıl yapılır: hata ayıklama için SQL Server Izinleri ayarlama](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [Hata Ayıklayıcısı Ayarları ve Hazırlığı](../debugger/debugger-settings-and-preparation.md)
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)