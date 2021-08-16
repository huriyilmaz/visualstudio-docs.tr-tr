---
title: Visual Studio |'de DirectX 12 desteği Microsoft Docs
description: Tam grafik hata ayıklama deneyimi için DirectX 12 kullanıcılarının Windows PIX kullanmaları önerilir
ms.date: 09/29/2020
ms.topic: conceptual
author: davidcongruili
ms.author: davidli1
manager: mluparu
ms.workload:
- multiple
ms.openlocfilehash: 7a3ba160023f1bc3b3fe6c2e78ef548c4495d47bc6e102a462950223a7caa52f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121419799"
---
# <a name="directx-12-support-in-visual-studio"></a>Visual Studio'de DirectX 12 Desteği

## <a name="directx-12-support"></a>DirectX 12 Desteği

Visual Studio Grafik Tanılama DirectX 12 oyunlarını desteklemez. Tam DirectX 12 desteğiyle grafik hata ayıklaması için Visual Studio üzerinde *PIX Windows.* 

Windows PIX, uzak özelliklere sahip bir performans ayarlama ve hata ayıklama aracıdır. Windows PIX, grafik hata ayıklama ihtiyaçlarınıza uygun yedi ana özellik sunar. GPU yakalamaları ile Direct3D 12 grafik işleme performansının hata ayıklaması ve analiz etme. Zamanlama yakalamaları ile oyun tarafından gerçekleştirilen tüm CPU ve GPU çalışmalarının performansını ve iş parçacığını anlama. Dosya IO yakalamaları ile başlığınıza ilişkin disk IO düzenleri ve paket düzenindeki verimleri belirleme.

üzerinde PIX ile grafik hata ayıklama [**yolculuğunuza Windows.**](https://aka.ms/PIXonWindows)

[**PIX'i Windows**](https://aka.ms/downloadPIX) veya [ **Belgeleri'ne bakın.**](https://devblogs.microsoft.com/pix/documentation/)

## <a name="pix-on-windows"></a>Windows üzerinde PIX

Windows PIX yedi ana işlem modu sunar:
1. **Direct3D** 12 grafik işleme performansının hata ayıklaması ve analizi için GPU yakalamaları.
2. **Oyun tarafından gerçekleştirilen** tüm CPU ve GPU çalışmalarının performansını ve iş parçacığını anlamak ve GPU bellek kullanımını izlemek için zamanlama yakalamaları.
3. **İşlev Özeti, her** bir işlevin ne kadar süreyle çalıştırı ve her biri çağrılma sıklı hakkında bilgi toplar.
4. **Çağrıgraf yakalamaları** tek bir işlevin yürütülmesini izler.
5. **Bellek Ayırma yakalamaları,** oyun tarafından yapılan bellek ayırmaları hakkında içgörü sağlar.
6. **Dosya IO yakalamaları,** başlığınıza ilişkin disk IO düzenleri ve paket düzenindeki verimleri tanımlamanıza yardımcı olur.
7. **Sistem İzleyicisi,** oyun çalışırken gerçek zamanlı sayaç verilerini görüntüler.

Windows'da PIX'Windows ayrıntılı bir video tanıtımı burada [ **mevcuttur**](https://www.youtube.com/playlist?list=PLeHvwXyqearWuPPxh6T03iwX-McPG5LkB)
