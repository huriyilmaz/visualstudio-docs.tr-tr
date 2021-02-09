---
title: Spy + + Başlat | Microsoft Docs
description: Bir çözümde hata ayıklamak istediğinizde, Visual Studio 'dan veya bir komut isteminden Spy + + aracının nasıl başlatılacağını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/16/2018
ms.topic: how-to
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0e8b1125534e52c810f97c91bd00ea53dfd3d6de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896630"
---
# <a name="how-to-start-spy"></a>Nasıl Yapılır: Spy++ Hizmetini Başlatma

Spy + + ' ya Visual Studio 'dan veya bir komut isteminde başlatabilirsiniz.

 Spy + + ' ı başlattığınızda, bilgisayarda değişiklik yapma izni istemek üzere bir ileti görüntülenirse **Evet**' i seçin.

> [!NOTE]
> Spy + + ' un yalnızca bir örneğini çalıştırabilirsiniz. İkinci bir örnek başlatmaya çalışırsanız, yalnızca şu anda çalışan örneğin odağı almasına neden olur.

## <a name="prerequisites"></a>Önkoşullar

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

2. **spyxx.exe** girin.

## <a name="see-also"></a>Ayrıca bkz.
- [Spy++ Kullanma](../debugger/using-spy-increment.md)
- [Spy++ Görünümleri](../debugger/spy-increment-views.md)
- [Spy++ Başvurusu](../debugger/spy-increment-reference.md)
