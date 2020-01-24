---
title: "Nasıl yapılır: Spy + + ' yı başlatma | Microsoft Docs"
ms.date: 12/16/2018
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70874d70dd5f845e7b627f2aeb7ae51bafe45995
ms.sourcegitcommit: 7b07e7b5e06e2e13f622445c568b78a284e1a40d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542626"
---
# <a name="how-to-start-spy"></a>Nasıl Yapılır: Spy++ Hizmetini Başlatma

Spy + + ' ya Visual Studio 'dan veya bir komut isteminde başlatabilirsiniz.

 Spy + + ' ı başlattığınızda, bilgisayarda değişiklik yapma izni istemek üzere bir ileti görüntülenirse **Evet**' i seçin.

> [!NOTE]
> Spy + + ' un yalnızca bir örneğini çalıştırabilirsiniz. İkinci bir örnek başlatmaya çalışırsanız, yalnızca şu anda çalışan örneğin odağı almasına neden olur.

## <a name="prerequisites"></a>Prerequisites

Spy + + aşağıdaki bileşenleri gerektirir. **Tek tek bileşenler** sekmesini seçerek ve ardından aşağıdaki bileşenleri seçerek Visual Studio yükleyicisi bu bileşenleri seçebilirsiniz.

* Hata ayıklama ve test altında  **C++ profil oluşturma araçları ' nı seçin.**
* Geliştirme Etkinlikleri altında,  **C++ temel Özellikler ' i seçin**

Herhangi bir değişiklik yaptıysanız, bu bileşenleri yüklemek için istemleri izleyin.

## <a name="start-spy-from-visual-studio"></a>Visual Studio 'dan Spy + + Başlat

**Araçlar** menüsünde **Spy + +** ' yı seçin.

Spy + + bağımsız olarak çalıştığı için, başlattıktan sonra Visual Studio 'Yu kapatabilirsiniz.

> [!NOTE]
> Spy + + ile iletileri günlüğe kaydettiğinizde, işletim sisteminin daha yavaş çalışmasına neden olabilir.

## <a name="start-spy-at-a-command-prompt"></a>Komut isteminde Spy + + ' yı Başlat

1. Bir komut Istemi penceresinde dizinleri, spyxx. exe dosyasını içeren klasör olarak değiştirin. Genellikle, bu klasörün yolu... *Visual Studio yükleme klasörü*\Common7\Tools\\\\.

2. **Spyxx. exe**girin.

## <a name="see-also"></a>Ayrıca bkz.
- [Spy++ kullanma](../debugger/using-spy-increment.md)
- [Spy++ Görünümleri](../debugger/spy-increment-views.md)
- [Spy++ Başvurusu](../debugger/spy-increment-reference.md)
