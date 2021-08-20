---
title: DLL dosyasından hata Project | Microsoft Docs
description: Proje özelliklerinde çağıran uygulamayı belirterek bir DLL projesinin hata ayıklamasını projenin kendisinde başlatabilirsiniz. Ayrıntılar için bu makaleye bakın.
ms.custom: SEO-VS-2020
ms.date: 3/30/2021
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 61599a878d73ab188ee8e05bf7f1cf5c314ac42f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120965"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio-c-c-visual-basic-f"></a>Nasıl bilinir: Visual Studio'da DLL projesinde hata ayıklama (C#, C++, Visual Basic, F#)

DLL projesinde hata ayıklamanın bir yolu, DLL proje özelliklerinde çağıran uygulamayı belirtmektir. Ardından DLL projesinin kendisinde hata ayıklamaya başlayabilirsiniz. Bu yöntemin çalışması için uygulamanın, yapılandırmış olduğu konumdaki DLL'yi çağırmalıdır. Uygulama DLL'nin farklı bir sürümünü bulursa ve yüklerse, bu sürüm kesme noktalarınızı içermez. DLL'lerde hata ayıklamaya yönelik diğer yöntemler için bkz. [DLL projelerinde hata ayıklama.](../debugger/debugging-dll-projects.md)

Yönetilen uygulamanız yerel DLL'i çağırıyorsa veya yerel uygulamanız yönetilen DLL'i çağırıyorsa, hem DLL'de hem de çağıran uygulamada hata ayıkabilirsiniz. Daha fazla bilgi için [bkz. Karma modda hata ayıklama.](../debugger/how-to-debug-in-mixed-mode.md)

Yerel ve yönetilen DLL projelerinin çağıran uygulamaları belirtmek için farklı ayarları vardır.

## <a name="specify-a-calling-app-in-a-native-dll-project"></a>Yerel DLL projesinde bir çağırma uygulaması belirtme

1. içinde C++ DLL projesini **Çözüm Gezgini.** Özellikler simgesini **seçin,** Alt Enter  + **tuşuna basın** veya sağ tıklar ve Özellikler'i **seçin.**

1. Özellik **\<Project> Sayfaları iletişim** kutusunda, pencerenin üst kısmında yer alan **Yapılandırma** alanı'nın Hata Ayıkla olarak ayarlanmış olduğundan **emin olun.**

1. Yapılandırma **Özellikleri Hata**  >  **Ayıklama'ya tıklayın.**

1. Başlat için **Hata Ayıklayıcısı listesinde** Yerel Hata **Ayıklayıcısı'Windows** Veya Uzak Hata **Ayıklayıcısı'Windows seçin.**

1. Komut **veya** Uzak **Komut kutusuna,** çağrıyı yapılan uygulamanın tam yolunu ve dosya adını (örneğin, bir *.exe* ekleyin.

   ![Hata ayıklama Özellikler penceresi](../debugger/media/dbg-debugging-properties-dll.png "Hata ayıklama Özellikler penceresi")

1. Gerekli program bağımsız değişkenlerini Komut Bağımsız **Değişkenleri kutusuna** ekleyin.

1. **Tamam**’ı seçin.

## <a name="specify-a-calling-app-in-a-managed-dll-project"></a>Yönetilen DLL projesinde bir çağırma uygulaması belirtme

1. içinde C# veya Visual Basic DLL **projesini Çözüm Gezgini.** Özellikler simgesini **seçin,** Alt Enter  + **tuşuna basın** veya sağ tıklar ve Özellikler'i **seçin.**

1. Pencerenin üst kısmında **yer alan Yapılandırma** alanı'nın Hata Ayıkla olarak ayarlanmış olduğundan emin **olun.**

1. Başlat **eylemi altında:**

   - Daha .NET Framework için Dış programı başlat'ı **seçin** ve çağıran uygulamanın tam yolunu ve adını ekleyin.

   - Veya Tarayıcıyı **URL ile başlat'ı** seçin ve yerel uygulamanın URL'ASP.NET doldurun.

   - .NET Core URL'leri için **Hata Ayıklama** Özellikleri sayfası farklıdır. Başlat **açılan** listesinde **Yürütülebilir'i** seçin ve ardından Yürütülebilir alanına çağıran uygulamanın tam yolunu ve **adını** ekleyin.

1. Gerekli komut satırı bağımsız değişkenlerini Komut satırı **bağımsız değişkenleri veya Uygulama bağımsız** değişkenleri **alanına** ekleyin.

   ![C# Hata Ayıklama Özellikler penceresi](../debugger/media/dbg-debugging-properties-dll-csharp.png "C# Hata Ayıklama Özellikler penceresi")

1. Değişiklikleri **kaydetmek**  >  **için Seçilen Öğeleri Dosya Kaydet** veya **Ctrl** + **S** tuşlarını kullanın.

## <a name="debug-from-the-dll-project"></a>DLL projesinde hata ayıklama

1. DLL projesinde kesme noktaları ayarlayın.

1. DLL projesine sağ tıklayın ve Başlangıç Olarak **Ayarla'yı Project.**

1. Çözüm Yapılandırması **alanı'nın Hata** Ayıkla olarak ayarlanmış **olduğundan emin olun.** **F5 tuşuna** basın, yeşil Başlat **okuna** tıklayın veya Hata Ayıklama Başlat **Hata**  >  **Ayıklama'yı seçin.**

Ek ipuçları:

- Hata ayıklama kesme noktalarınıza isabetzse DLL çıkışının (varsayılan olarak *\<project> \Debug* klasörü) çağıran uygulamanın çağıran konum olduğundan emin olun.

- Yerel DLL'den yönetilen bir çağrı uygulamasında koda (veya tam tersi) gitmek için karma mod hata [ayıklamasını etkinleştirin.](../debugger/how-to-debug-in-mixed-mode.md)

- Bazı senaryolarda, hata ayıklayıcıya kaynak kodu nerede buluymalarını söylemenizi gerektirebilirsiniz. Daha fazla bilgi için [bkz. Yüklenen Sembol Yok/Kaynak Yüklenmedi sayfalarını kullanma.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#use-the-no-symbols-loadedno-source-loaded-pages)

## <a name="see-also"></a>Ayrıca bkz.
- [DLL projelerinde hata ayıklama](../debugger/debugging-dll-projects.md)
- [C# hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)
