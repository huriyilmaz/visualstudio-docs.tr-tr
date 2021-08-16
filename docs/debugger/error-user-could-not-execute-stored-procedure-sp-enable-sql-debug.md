---
description: Saklı Yordam sp_enable_sql_debug sunucuda yürütülemdi.
title: Kullanıcı Saklı Yordam Yürüte sp_enable_sql_debug | Microsoft Docs
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

Saklı Yordam sp_enable_sql_debug sunucuda yürütülemdi. Bunun nedeni:

- Bağlantı sorunu. Sunucuyla kararlı bir bağlantınız olması gerekir.

- Sunucuda gerekli izinlerin olmaması. SQL Server 2005'te hata ayıklamak için hem Visual Studio çalıştıran hesabın hem de SQL Server'a bağlanmak için kullanılan hesabın sysadmin rolünün üyesi olması gerekir. SQL Server'a bağlanmak için kullanılan hesap, Windows kullanıcı hesabınız (Windows kimlik doğrulaması kullanıyorsanız) veya kullanıcı kimliği ve parolası olan bir hesaptır (SQL kullanıyorsanız).

Daha fazla bilgi için, [bkz. How to: Set SQL Server Permissions for Debugging](/previous-versions/w1bhybwz(v=vs.100)).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıllı: Hata Ayıklama SQL Server İzinlerini Ayarlama](/previous-versions/w1bhybwz(v=vs.100))
- [Hata Ayıklama SQL Ayarlama](/previous-versions/visualstudio/visual-studio-2010/s4sszxst\(v\=vs.100\))
