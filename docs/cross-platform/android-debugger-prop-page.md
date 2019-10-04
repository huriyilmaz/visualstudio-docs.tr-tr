---
title: Android hata ayıklayıcı özellikleriC++() | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
author: corob-msft
ms.author: corob
manager: jillfra
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 0a052223fe7acac87acf15c5c5091c774451e4e4
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950628"
---
# <a name="android-debugger-properties"></a>Android hata ayıklayıcı özellikleri

Özellik | Açıklama | Yapabileceği
--- | ---| ---
Hata ayıklayıcı türü | Hata ayıklamanın hangi kod türünde olduğunu belirtir. | **Yalnızca yerel**<br>**Yalnızca Java**<br>
Hata ayıklama hedefi | Hata ayıklama için kullanılacak öykünücüyü veya cihazı belirtir. Hiçbir öykünücü çalışmıyorsa, lütfen bir cihaz başlatmak için ' Android sanal cihazı (AVD) Yöneticisi ' ni kullanın.
Başlatılacak paket | Hata ayıklaması yapılacak *. apk* konumunu belirtir. Uygulamanın hataları ayıklandığında belirli bir paketin (APK) başlatılması gerektiğini belirtmek için bu seçeneği belirleyin.
Başlatma etkinliği | Uygulamayı başlatmak için kullanılacak Android etkinliği, bildirimde kullanılan bir ile eşleşmelidir. *AndroidManifest. xml* dosyasından listeyi almak ve dinamik olarak doldurmak için Uygula ' ya basın.
Ek sembol arama yolları | Hata ayıklama sembolleri için ek arama yolu.
Ek Java kaynağı arama yolları | Java kaynak dosyaları için ek arama yolları. (Yalnızca hata ayıklayıcı türü yalnızca Java olduğunda geçerlidir.)
