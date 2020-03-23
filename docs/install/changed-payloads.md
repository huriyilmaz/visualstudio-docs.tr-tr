---
title: Paket yükleri bir sürümden sonra değiştiğinde
description: Bir düzen oluştururken, paket yükyüklerini bir sürüm gönderildikten sonra değiştirip değiştirmediğini nasıl belirleyemeye cereyin.
ms.date: 05/22/2019
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: dec1478314e752ddace8fae822747e7c8e328b70
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114580"
---
# <a name="package-payload-changes"></a>Paket yükü değişiklikleri

Bazı paket yüklerinin, bir sürüm gönderildikten sonra değiştirilmesine izin verilir. Siz veya bir başkası bir düzen oluşturduğunda, bu davranış, bir düzenin ne zaman oluşturulduğuna bağlı olarak farklı düzen içeriğine neden olabilir.

## <a name="verify-that-a-layout-includes-package-payload-changes"></a>Bir düzenin paket yükü değişiklikleri içerdiğini doğrulama

Daha önce oluşturulmuş olan düzenin, gönderilen sürümden sonra değiştirilen paket yüklerini edinip edinmediğini şu şekilde belirleyebilirsiniz:

1. Kurulum günlüğünü açın. Günlük genellikle düzen `%TEMP%\dd_setup_[date].log` işleminin biçimolarak `[date]` `yyyyMMddHHmmss` başlatıldığı yerdir.

2. Günlükte aşağıdaki metin gibi yapılandırılan bir satır arayın:

    `Falling back to signature and signer check because hash verification returned HashMismatch for path: [path]`

3. Ardından, indirmenin [yol] için başarılı olduğunu gösteren daha sonra günlükte satırları arayın. Aşağıdaki metne benzer görünebilirler:

    `Download of [url] succeeded using engine 'WebClient'`

    `END: Downloading [url] to [path]`

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'nun ağ yüklemesini oluşturma](create-a-network-installation-of-visual-studio.md)
* [Visual Studio'nun ağa dayalı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
