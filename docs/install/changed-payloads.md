---
title: Bir sürümden sonra paket yükleri değiştiğinde
description: Bir düzen oluştururken, bir yayın zaten gönderildikten sonra paket yüklerin değişip değişmediğini belirlemeyi öğrenin.
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
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114580"
---
# <a name="package-payload-changes"></a>Paket yükü değişiklikleri

Bir yayın zaten sevk edildikten sonra bazı paket yüklerin değiştirilmesine izin verilir. Siz veya başka biri bir düzen oluşturduğunda, bu davranış, bir düzenin ne zaman oluşturulduğuna bağlı olarak farklı düzen içeriğine yol açabilir.

## <a name="verify-that-a-layout-includes-package-payload-changes"></a>Bir düzenin paket yükü değişikliklerini içerdiğini doğrulama

Daha önce oluşturulmuş olan düzenin, yayın gönderildikten sonra değiştirilen paket yüklerini elde ettiği belirlenir:

1. Kurulum günlüğünü açın. Günlük genellikle `[date]` Düzen işleminin `yyyyMMddHHmmss` biçimde başlatıldığı `%TEMP%\dd_setup_[date].log`.

2. Günlükte aşağıdaki metin gibi yapılandırılmış bir satırı arayın:

    `Falling back to signature and signer check because hash verification returned HashMismatch for path: [path]`

3. Daha sonra, [Path] için indirme başarılı olduğunu belirten günlükte daha sonra satırları arayın. Şu metne benzer görünebilir:

    `Download of [url] succeeded using engine 'WebClient'`

    `END: Downloading [url] to [path]`

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'nun bir ağ oluşturun](create-a-network-installation-of-visual-studio.md)
* [Visual Studio'nun ağ tabanlı yüklemesini güncelleştirme](update-a-network-installation-of-visual-studio.md)
