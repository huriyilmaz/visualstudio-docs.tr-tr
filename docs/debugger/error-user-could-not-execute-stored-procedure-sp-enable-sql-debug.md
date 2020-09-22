---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8131c7b16205b308e04b621dd1fcb536ba94c14
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852432"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>Hata: Kullanıcı sp_enable_sql_debug Saklı Yordamını Yürütemedi

Saklı yordam sp_enable_sql_debug sunucuda yürütülemedi. Bunun nedeni şunlar olabilir:

- Bir bağlantı sorunu. Sunucuyla kararlı bir bağlantınız olması gerekir.

- Sunucuda gerekli izinlerin bulunmaması. SQL Server 2005 ' de hata ayıklamak için, hem Visual Studio çalıştıran hesap hem de SQL Server bağlanmak için kullanılan hesap sysadmin rolünün üyeleri olmalıdır. SQL Server bağlanmak için kullanılan hesap, Windows kullanıcı hesabıdır (Windows kimlik doğrulaması kullanıyorsanız) veya Kullanıcı KIMLIĞI ve parolası olan bir hesap (SQL kimlik doğrulaması kullanıyorsanız).

Daha fazla bilgi için bkz. [nasıl yapılır: hata ayıklama için SQL Server Izinleri ayarlama](/previous-versions/w1bhybwz(v=vs.100)).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: hata ayıklama için SQL Server Izinleri ayarlama](/previous-versions/w1bhybwz(v=vs.100))
- [SQL hata ayıklamayı ayarlama](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))