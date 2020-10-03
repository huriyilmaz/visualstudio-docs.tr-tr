---
title: Visual Studio 'da DirectX 12 desteği | Microsoft Docs
description: DirectX 12 kullanıcılarının tam bir grafik hata ayıklama deneyimi için Windows 'da PıX kullanılması önerilir
ms.date: 09/29/2020
ms.topic: conceptual
author: davidcongruili
ms.author: davidli1
manager: mluparu
ms.workload:
- multiple
ms.openlocfilehash: 9dbc52a0233abe467da4d41af0134663bc7cd9df
ms.sourcegitcommit: a1cb4e2025045c2ad79167645c4c0f33b94b1152
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91671399"
---
# <a name="directx-12-support-in-visual-studio"></a>Visual Studio 'da DirectX 12 desteği

## <a name="directx-12-support"></a>DirectX 12 desteği

Visual Studio Grafik Tanılama DirectX 12 oyunları desteklemez. Tam DirectX 12 desteğiyle grafik hata ayıklaması için, Visual Studio *Windows üzerinde PIX*önerir. 

Windows üzerinde PıX, uzak yeteneklere sahip bir performans ayarlama ve hata ayıklama aracıdır. Windows üzerinde PıX, grafik hata ayıklama ihtiyaçlarınıza uyan yedi ana özellik sunar. GPU yakalamalarında Direct3D 12 grafik işlemenin performansını hata ayıklayın ve çözümleyin. Zamanlama yakalamaları sayesinde oyununuzu tarafından gerçekleştirilen tüm CPU ve GPU çalışmalarını performansını ve iş parçacığı oluşturmayı anlayın. Başlığınızın disk GÇ desenlerinde ve dosya GÇ yakalamaları ile paket düzeninde verimsizlikleri ' i belirler.

[**Windows üzerinde PIX**](https://aka.ms/PIXonWindows)ile grafik hata ayıklama yolculuğuna basın.

[**Windows ÜZERINDE PIX indirin**](https://aka.ms/downloadPIX) veya [ **belgeleri görüntüleyin**.](https://devblogs.microsoft.com/pix/documentation/)

## <a name="pix-on-windows"></a>Windows üzerinde PıX

Windows üzerinde PıX Özellikler yedi temel işlem modu:
1. **GPU** , hata ayıklama ve Direct3D 12 grafik işleme performansını analiz etmek için yakalar.
2. **Zamanlama** , oyununuza göre GERÇEKLEŞTIRILEN tüm CPU ve GPU işleri için performans ve iş parçacığı OLUŞTURMAYı ve GPU bellek kullanımını izlemek için yakalar.
3. **Işlev Özeti** , her bir işlevin ne kadar süreyle çalıştığı ve ne sıklıkta çağrıldığı hakkında bilgi birikmesini yakalar.
4. **Callgraph** , tek bir işlevin yürütülmesini izlemeyi yakalar.
5. **Bellek ayırma yakalamaları** , oyununuzun yaptığı bellek ayırmaları hakkında öngörüler sağlar.
6. **Dosya GÇ yakalamaları** , başlığınızın disk GÇ desenleri ve paket düzeninde verimsizlikleri belirlemenize yardımcı olur.
7. Bir oyun çalışırken **Sistem İzleyicisi** gerçek zamanlı sayaç verilerini görüntüler.

Windows üzerinde PıX 'e giriş hakkında ayrıntılı bir video, [ **burada** bulunabilir](https://www.youtube.com/playlist?list=PLeHvwXyqearWuPPxh6T03iwX-McPG5LkB)
