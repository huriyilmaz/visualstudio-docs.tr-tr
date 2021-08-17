---
description: bu hata, bir Transact-SQL veya sqlclr yordamında hata ayıklamaya çalışırken ve hata ayıklayıcı SQL Server hata ayıklama mesajları almadığında oluşur.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f769f7af0412b19be1addd0b556a647c5d8041bd9b3c3f48e0022315d3519bc9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121419929"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>Hata: Transact-SQL yürütmesi hata ayıklaması yapılmadan sonlandı

bu hata, bir Transact-SQL veya sqlclr yordamında hata ayıklamaya çalışırken ve hata ayıklayıcı SQL Server hata ayıklama mesajları almadığında oluşur.

bu sorun, ağ sorunlarından veya SQL Server sorunlarından kaynaklanıyor olabilir, ancak olası nedeni bir izin sorunudur.

Dahil olmak üzere iki hesap vardır:

- Uygulama hesabı, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] olarak çalışan kullanıcı hesabıdır.

- Bağlantı hesabı, SQL Server bağlantısını yapmak için kullanılan kimliktir. bu hesap, bağlantı SQL kimlik doğrulaması kullanıyor gibi Visual Studio çalıştığı kimlikle aynı değildir.

  SQL hata ayıklaması, uygulama hesabının bağlantı hesabı ile eşleşmesi veya bir sysadmin olması gerekir.

  sa gibi SQL hesap adı kullanıyorsanız, uygulama hesabının SQL Server sysadmin olarak ayarlanması gerekir. varsayılan olarak, SQL sunucusunun çalıştığı makinedeki yöneticiler sysadmins SQL Server.

  Bu hatayı düzeltmek için şunları yapmanız gerekebilir:

  - İzin ayarlarınızı doğrulayın. daha fazla bilgi için bkz. [nasıl yapılır: hata ayıklama için SQL Server izinleri ayarlama](/previous-versions/w1bhybwz(v=vs.100)).

  - doğru ayarlandıysa hata ayıklamanın SQL emin olun.

  - Ağınız veya veritabanı yöneticinizle görüşün.

## <a name="see-also"></a>Ayrıca bkz.

- [SQL hata ayıklamayı ayarlama](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [nasıl yapılır: hata ayıklama için SQL Server izinleri ayarlama](/previous-versions/w1bhybwz(v=vs.100))
- [hata ayıklayıcı Ayarlar ve hazırlığı](../debugger/debugger-settings-and-preparation.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
