---
title: Bir yayından sonra paket yüklerini değiştirdikten sonra
description: Düzen oluştururken, bir yayın gönderildikten sonra paket yüklerini değiştirmenin nasıl olduğunu belirlemeyi öğrenin.
ms.date: 05/22/2019
ms.topic: how-to
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 22201f48f05e2ba6a40ea538ed9795b04fda7e54f755cb241f8570520a4b4068
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121386465"
---
# <a name="package-payload-changes"></a>Paket yükü değişiklikleri

Bir yayın gönderildikten sonra bazı paket yüklerini değiştirebilirsiniz. Siz veya başka biri bir düzen oluşturulduğunda, bu davranış bir düzenin ne zaman oluşturulduğunda bağlı olarak farklı düzen içeriğine neden olabilir.

## <a name="verify-that-a-layout-includes-package-payload-changes"></a>Düzende paket yükü değişiklikleri olduğunu doğrulayın

Daha önce oluşturulan düzenin, yayın gönderildikten sonra değiştirilen paket yüklerini aldırarak alın olup olmadığını nasıl belirleyebilirsiniz:

1. Kurulum günlüğünü açın. Günlük genellikle düzen `%TEMP%\dd_setup_[date].log` işlemi biçiminde başladığı `[date]` `yyyyMMddHHmmss` yerdedir.

2. Günlükte aşağıdaki metin gibi yapılandırılmış bir satıra bakın:

    `Falling back to signature and signer check because hash verification returned HashMismatch for path: [path]`

3. Ardından günlüğün devamlarında [path] için indirmenin başarılı olduğunu belirten satırlarına bakın. Aşağıdaki metne benzer olabilir:

    `Download of [url] succeeded using engine 'WebClient'`

    `END: Downloading [url] to [path]`

## <a name="see-also"></a>Ayrıca bkz.

* [Ağ yüklemesi oluşturma Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Ağ tabanlı yüklemesini güncelleştirme Visual Studio](update-a-network-installation-of-visual-studio.md)
