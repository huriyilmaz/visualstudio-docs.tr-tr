---
title: Spy++ | Microsoft Docs
description: Bir çözümde hata ayıklamak Visual Studio bir komut isteminden spy++ aracını başlatmayı biliyorsunuz.
ms.custom: SEO-VS-2020
ms.date: 12/16/2018
ms.topic: how-to
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 470d9676ed2bb908b04f4bbddc905ddede97802d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128123"
---
# <a name="how-to-start-spy"></a>Nasıl Yapılır: Spy++ Hizmetini Başlatma

Spy++ 'i bir komut Visual Studio komut isteminden başlatabilirsiniz.

 Spy++'ı başlatınca, bilgisayarda değişiklik yapma iznini istemek için bir ileti görüntüleniyorsa Evet'i **seçin.**

> [!NOTE]
> Spy++'ın yalnızca bir örneğini çalıştırarak. İkinci bir örneği başlatmayı denersiniz, bu yalnızca o anda çalışan örneğin odak noktası elde uzer.

## <a name="prerequisites"></a>Önkoşullar

Spy++ aşağıdaki bileşenleri gerektirir. Bağımsız Bileşenler sekmesini ve ardından Visual Studio Yükleyicisi bileşenleri  seçerek bu bileşenleri listeden seçin.

* Hata ayıklama ve test altında **C++ profil oluşturma araçları'ı seçin**
* Geliştirme etkinlikleri'nin altında **C++ temel özellikleri'i seçin**

Herhangi bir değişiklik yaptıysanız, bu bileşenleri yüklemek için istemleri izleyin.

## <a name="start-spy-from-visual-studio"></a>Visual Studio'dan Spy++ başlatma

Araçlar menüsünde **Spy++** **öğesini seçin.**

Spy++ bağımsız olarak çalıştırılalı olduğundan, başladıktan sonra Visual Studio.

> [!NOTE]
> İletileri Spy++ ile günlüğe kaydedilirken, bu durum işletim sisteminin daha yavaş performansa neden olabilir.

## <a name="start-spy-at-a-command-prompt"></a>Komut isteminde Spy++ başlatma

1. Bir Komut İstemi penceresinde dizinleri, dizinleri yeni bir spyxx.exe. Bu klasörün yolu genellikle olur. \\ *Visual Studio klasörü*\Common7\Tools \\ .

2. **spyxx.exe.**

## <a name="see-also"></a>Ayrıca bkz.
- [Spy++ Kullanma](../debugger/using-spy-increment.md)
- [Spy++ Görünümleri](../debugger/spy-increment-views.md)
- [Spy++ Başvurusu](../debugger/spy-increment-reference.md)
