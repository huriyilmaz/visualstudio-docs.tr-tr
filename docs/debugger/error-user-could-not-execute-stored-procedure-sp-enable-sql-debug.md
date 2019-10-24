---
title: 'Hata: Kullanıcı, sp_enable_sql_debug saklı yordamını çalıştıramadı | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: 3bdc6ecb03572d824f6e3b887090d67be416cdef
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736546"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>Hata: Kullanıcı sp_enable_sql_debug Saklı Yordamını Yürütemedi

Saklı yordam sp_enable_sql_debug sunucuda yürütülemedi. Bunun nedeni şunlar olabilir:

- Bir bağlantı sorunu. Sunucuyla kararlı bir bağlantınız olması gerekir.

- Sunucuda gerekli izinlerin bulunmaması. SQL Server 2005 ' de hata ayıklamak için, hem Visual Studio çalıştıran hesap hem de SQL Server bağlanmak için kullanılan hesap sysadmin rolünün üyeleri olmalıdır. SQL Server bağlanmak için kullanılan hesap, Windows kullanıcı hesabıdır (Windows kimlik doğrulaması kullanıyorsanız) veya Kullanıcı KIMLIĞI ve parolası olan bir hesap (SQL kimlik doğrulaması kullanıyorsanız).

Daha fazla bilgi için bkz. [nasıl yapılır: hata ayıklama için SQL Server Izinleri ayarlama](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: hata ayıklama için SQL Server Izinleri ayarlama](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)
- [SQL hata ayıklamayı ayarlama](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))