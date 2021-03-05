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
ms.workload:
- multiple
ms.openlocfilehash: 8c7597acb201aa810d34fe0df0f0aebbbd2f70fe
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146294"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>Hata: Kullanıcı sp_enable_sql_debug Saklı Yordamını Yürütemedi

Saklı yordam sp_enable_sql_debug sunucuda yürütülemedi. Bunun nedeni şunlar olabilir:

- Bir bağlantı sorunu. Sunucuyla kararlı bir bağlantınız olması gerekir.

- Sunucuda gerekli izinlerin bulunmaması. SQL Server 2005 ' de hata ayıklamak için, hem Visual Studio çalıştıran hesap hem de SQL Server bağlanmak için kullanılan hesap sysadmin rolünün üyeleri olmalıdır. SQL Server bağlanmak için kullanılan hesap, Windows kullanıcı hesabıdır (Windows kimlik doğrulaması kullanıyorsanız) veya Kullanıcı KIMLIĞI ve parolası olan bir hesap (SQL kimlik doğrulaması kullanıyorsanız).

Daha fazla bilgi için bkz. [nasıl yapılır: hata ayıklama için SQL Server Izinleri ayarlama](/previous-versions/w1bhybwz(v=vs.100)).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: hata ayıklama için SQL Server Izinleri ayarlama](/previous-versions/w1bhybwz(v=vs.100))
- [SQL hata ayıklamayı ayarlama](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))
