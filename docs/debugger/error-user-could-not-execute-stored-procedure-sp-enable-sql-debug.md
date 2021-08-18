---
description: Saklı yordam sp_enable_sql_debug sunucuda yürütülemedi.
title: Kullanıcı, saklı yordamı çalıştıramadı sp_enable_sql_debug | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: df25fb20fcf824c09b46a13eb704015d196a2930
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097174"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>Hata: Kullanıcı sp_enable_sql_debug Saklı Yordamını Yürütemedi

Saklı yordam sp_enable_sql_debug sunucuda yürütülemedi. Bunun nedeni şunlar olabilir:

- Bir bağlantı sorunu. Sunucuyla kararlı bir bağlantınız olması gerekir.

- Sunucuda gerekli izinlerin bulunmaması. SQL Server 2005 ' de hata ayıklamak için Visual Studio çalıştıran hesabın ve SQL Server bağlanmak için kullanılan hesabın sysadmin rolünün üyeleri olması gerekir. SQL Server bağlanmak için kullanılan hesap Windows kullanıcı hesabıdır (Windows kimlik doğrulaması kullanıyorsanız) ya da kullanıcı kimliği ve parolası olan bir hesap (SQL kimlik doğrulaması kullanıyorsanız).

daha fazla bilgi için bkz. [nasıl yapılır: hata ayıklama için SQL Server izinleri ayarlama](/previous-versions/w1bhybwz(v=vs.100)).

## <a name="see-also"></a>Ayrıca bkz.

- [nasıl yapılır: hata ayıklama için SQL Server izinleri ayarlama](/previous-versions/w1bhybwz(v=vs.100))
- [SQL hata ayıklamayı ayarlama](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))
