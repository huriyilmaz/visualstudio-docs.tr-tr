---
title: Nasıl yapılır-Spy + + 'ı başlatma | Microsoft Docs
ms.date: 12/16/2018
ms.topic: how-to
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b659350adc39fd1088964976b8bcdef629bad44b
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349010"
---
# <a name="how-to-start-spy"></a>Nasıl Yapılır: Spy++ Hizmetini Başlatma

Spy + + ' ya Visual Studio 'dan veya bir komut isteminde başlatabilirsiniz.

 Spy + + ' ı başlattığınızda, bilgisayarda değişiklik yapma izni istemek üzere bir ileti görüntülenirse **Evet**' i seçin.

> [!NOTE]
> Spy + + ' un yalnızca bir örneğini çalıştırabilirsiniz. İkinci bir örnek başlatmaya çalışırsanız, yalnızca şu anda çalışan örneğin odağı almasına neden olur.

## <a name="prerequisites"></a>Ön koşullar

Spy + + aşağıdaki bileşenleri gerektirir. **Tek tek bileşenler** sekmesini seçerek ve ardından aşağıdaki bileşenleri seçerek Visual Studio yükleyicisi bu bileşenleri seçebilirsiniz.

* Hata ayıklama ve test altında **C++ profil oluşturma araçları** ' nı seçin.
* Geliştirme Etkinlikleri altında **C++ Core özellikleri** ' ni seçin.

Herhangi bir değişiklik yaptıysanız, bu bileşenleri yüklemek için istemleri izleyin.

## <a name="start-spy-from-visual-studio"></a>Visual Studio 'dan Spy + + Başlat

**Araçlar** menüsünde **Spy + +**' yı seçin.

Spy + + bağımsız olarak çalıştığı için, başlattıktan sonra Visual Studio 'Yu kapatabilirsiniz.

> [!NOTE]
> Spy + + ile iletileri günlüğe kaydettiğinizde, işletim sisteminin daha yavaş çalışmasına neden olabilir.

## <a name="start-spy-at-a-command-prompt"></a>Komut isteminde Spy + + ' yı Başlat

1. Bir komut Istemi penceresinde dizinleri spyxx.exe içeren klasör olarak değiştirin. Genellikle, bu klasörün yolu... \\ *Visual Studio yükleme klasörü*\Common7\Tools \\ .

2. **spyxx.exe**girin.

## <a name="see-also"></a>Ayrıca bkz.
- [Spy++ Kullanma](../debugger/using-spy-increment.md)
- [Spy++ Görünümleri](../debugger/spy-increment-views.md)
- [Spy++ Başvurusu](../debugger/spy-increment-reference.md)
