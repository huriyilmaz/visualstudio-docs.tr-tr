---
title: "Nasıl yapılır: Enstrümantasyonu Belirli DL'lerle Sınırlandırın | Microsoft Dokümanlar"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, runtime profiling control window
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 066262a3fae35e82904b011165813e9dd75d9987
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778823"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Nasıl yapılır: İzlemeyi belirli DLL'ler ile sınırlama

Instrumentation profil oluşturma yöntemini kullanarak, profil oluşturma verilerinin bir uygulamadaki bir veya daha fazla DL'yle toplanmasını sınırlayabilirsiniz. Bir uygulamada bir veya daha fazla DL profilini çıkarmak için, bir performans oturumu oluşturursunuz. hedef olarak *dll* dosyaları. Profilini çıkarmak istediğiniz DL'leri Visual Studio çözümünde veya bağımsız ikili dosyalarda proje olarak belirtebilirsiniz.

## <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Görsel Stüdyo çözümünde enstrümantasyonu belirli DL'lerle sınırlamak için

1. Visual Studio'da DLL içeren çözümü açın.

2. **Analiz** menüsünde, **Performans Sihirbazı Başlat'ı**seçin.

3. Profil oluşturma yöntemi olarak **Enstrümantasyon'u** seçin ve **sonra İleri'yi**tıklatın.

4. Aşağıdaki **mevcut hedeflerden hangisinde profil çıkarmak istersiniz?** *dll* proje ve sonra **İleri'yi**tıklatın.

5. Sihirbazdan çıkmak ve **Performans Gezgini** penceresinde yeni performans oturumunu görüntülemek için **Bitir'i** tıklatın.

6. **Hedefler'i** sağ tıklatın ve ardından **Hedef Proje Ekle'yi**seçin.

7. Hedef **Proje Ekle** listesinden, DLL'yi uygulamak için kullanmak istediğiniz çalıştırılabilir projeyi seçin.

     İsteğe bağlı. Profilini çıkarmak istediğiniz DLL projelerini ekleyebilirsiniz.

8. Eklenen bir proje için veri toplanmasını önlemek için projenin adını sağ tıklatın ve ardından **Enstrüman** onay kutusunu temizleyin.

## <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Bağımsız ikili olarak profillemek için belirli DL'leri belirtmek için

1. Visual Studio'yu açın.

2. **Analiz** menüsünde, **Performans Sihirbazı Başlat'ı**seçin.

3. Aşağıdaki **mevcut hedeflerden hangisinde profil çıkarmak istiyorsunuz,** **Profil dinamik bağlantı kitaplığı (. DLL)** ve sonra **İleri'yi**tıklatın.

4. Sihirbazın ikinci sayfasında aşağıdaki adımları gerçekleştirin:

    - Yol ve dosya adını yazın. **Dll yolunda**profilini çıkarmak istediğiniz *dll* dosyası . Ayrıca profil iletişim kutusuna **Dinamik bağlantı kitaplığında** dosyayı bulmak için elips düğmesini (...) tıklatabilirsiniz. Kopyayı belirtmeniz gerektiğini unutmayın. yürütülebilir tarafından başlatılacak *dll* dosyası (.* exe*) sonraki seçtiğiniz dosya.

    - Yürütülebilir yol ve dosya adını yazın (.* exe*) dosyasını kullanacak. *dll* **yürütülebilir yolda**. Ayrıca, **dosyayı başlatabilmek için Yürütülebilir'de** bulunan elips düğmesini (...) tıklatabilirsiniz.

    - İsteğe bağlı. **Komut satırı bağımsız değişkenlerinde**yürütülebilir dosyaya geçmek istediğiniz komut satırı bağımsız değişkenlerini yazın. Gerekirse, **Çalışma dizininde**uygulama nın çalışma dizinini belirtin.

    - **İleri**'ye tıklayın.

5. Profil oluşturma yöntemi olarak **Enstrümantasyon'u** seçin ve **sonra İleri'yi**tıklatın.

6. Sihirbazdan çıkmak ve **Performans Gezgini** penceresinde yeni performans oturumunu görüntülemek için **Bitir'i** tıklatın.

7. İsteğe bağlı. Daha fazla eklemek için . *dll* dosyaları, **Sağ** tıklayın Hedefler ve sonra **Hedef İkili ekle'yi**seçin. **Hedef İkili Ekle** iletişim kutusundan dosyaları seçin.

    > [!NOTE]
    > Çalıştırılabilir belirtin (.* exe*) DLs egzersizleri dosya.

## <a name="see-also"></a>Ayrıca bkz.

[Kontrol veri toplama](../profiling/controlling-data-collection.md)
[Nasıl yapılır: Enstrümantasyonu belirli işlevler ile sınırlandırın](../profiling/how-to-limit-instrumentation-to-specific-functions.md)
