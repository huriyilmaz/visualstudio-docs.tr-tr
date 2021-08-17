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
ms.openlocfilehash: 43a16ade834255622466ef3ba35359bcf465c8647a5f4a65a2b4498dc6545d1e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121454321"
---
# <a name="error-user-could-not-execute-stored-procedure-sp_enable_sql_debug"></a>Hata: Kullanıcı sp_enable_sql_debug Saklı Yordamını Yürütemedi

Saklı yordam sp_enable_sql_debug sunucuda yürütülemedi. Bunun nedeni şunlar olabilir:

- Bir bağlantı sorunu. Sunucuyla kararlı bir bağlantınız olması gerekir.

- Sunucuda gerekli izinlerin bulunmaması. SQL Server 2005 ' de hata ayıklamak için Visual Studio çalıştıran hesabın ve SQL Server bağlanmak için kullanılan hesabın sysadmin rolünün üyeleri olması gerekir. SQL Server bağlanmak için kullanılan hesap Windows kullanıcı hesabıdır (Windows kimlik doğrulaması kullanıyorsanız) ya da kullanıcı kimliği ve parolası olan bir hesap (SQL kimlik doğrulaması kullanıyorsanız).

daha fazla bilgi için bkz. [nasıl yapılır: hata ayıklama için SQL Server izinleri ayarlama](/previous-versions/w1bhybwz(v=vs.100)).

## <a name="see-also"></a>Ayrıca bkz.

- [nasıl yapılır: hata ayıklama için SQL Server izinleri ayarlama](/previous-versions/w1bhybwz(v=vs.100))
- [SQL hata ayıklamayı ayarlama](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))
