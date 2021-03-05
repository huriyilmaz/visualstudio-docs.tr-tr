---
description: Bu hata, bir Transact-SQL veya SQLCLR yordamını hata ayıklamaya çalışırken ve hata ayıklayıcı SQL Server hata ayıklama mesajları almadığında oluşur.
title: Transact-SQL yürütmesi hata ayıklama olmadan sona erdi | Microsoft Docs
ms.date: 11/08/2018
ms.topic: error-reference
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 40b0b89474b24e53c69df14894e50ee502c6eb9b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146502"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Hata: Transact-SQL yürütmesi hata ayıklaması yapılmadan sonlandı

Bu hata, bir Transact-SQL veya SQLCLR yordamını hata ayıklamaya çalışırken ve hata ayıklayıcı SQL Server hata ayıklama mesajları almadığında oluşur.

Bu sorun, ağ sorunlarından veya SQL Server sorunlarından kaynaklanıyor olabilir, ancak olası nedeni bir izin sorunudur.

Dahil olmak üzere iki hesap vardır:

- Uygulama hesabı, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] olarak çalışan kullanıcı hesabıdır.

- Bağlantı hesabı, SQL Server bağlantısını yapmak için kullanılan kimliktir. Bu hesap, bağlantı SQL kimlik doğrulaması kullanıyor gibi, Visual Studio 'Nun çalıştırdığı kimlikle aynı değildir.

  SQL hata ayıklaması, uygulama hesabının bağlantı hesabıyla eşleşmesi veya bir sysadmin olması gerekir.

  Sa gibi bir SQL hesap adı kullanıyorsanız, uygulama hesabının SQL Server sysadmin olarak ayarlanması gerekir. Varsayılan olarak, SQL Server 'ın üzerinde çalıştığı makinedeki Yöneticiler SQL Server sysadmins ' dir.

  Bu hatayı düzeltmek için şunları yapmanız gerekebilir:

  - İzin ayarlarınızı doğrulayın. Daha fazla bilgi için bkz. [nasıl yapılır: hata ayıklama için SQL Server Izinleri ayarlama](/previous-versions/w1bhybwz(v=vs.100)).

  - Doğru ayarlandıysa SQL hata ayıklamanın bulunduğundan emin olun.

  - Ağınız veya veritabanı yöneticinizle görüşün.

## <a name="see-also"></a>Ayrıca bkz.

- [SQL hata ayıklamayı ayarlama](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [Nasıl yapılır: hata ayıklama için SQL Server Izinleri ayarlama](/previous-versions/w1bhybwz(v=vs.100))
- [Hata ayıklayıcı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
