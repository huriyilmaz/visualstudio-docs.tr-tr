---
title: Ölçüm ölçümlerini Belirli URL'ler ile | Microsoft Docs
description: Profil oluşturma verisi toplamayı bir uygulamada bir veya daha fazla URL ile sınırlamak için ölçümleme profil oluşturma yöntemini kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, runtime profiling control window
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fcd80eb5501a86bd046a5917e2fc5ed9366f573f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141837"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Nasıl yapılır: İzlemeyi belirli DLL'ler ile sınırlama

Ölçüm aracı profil oluşturma yöntemini kullanarak, profil oluşturma verisi koleksiyonunu bir uygulamanın bir veya daha fazla DL'sinde sınırabilirsiniz. Bir uygulamada bir veya daha fazla URL profili oluşturmak için, içeren bir performans oturumu oluşturmanız gerekir. *hedef* olarak dll dosyaları. Profil oluşturmak istediğiniz URL'leri bir çözümde proje olarak Visual Studio bağımsız ikili dosyalar olarak belirtebilirsiniz.

## <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Ölçümlü araçları bir çözümde belirli VISUAL STUDIO sınırlamak için

1. Dll dosyasını içeren çözümü Visual Studio.

2. Analiz menüsünde **Performans** Sihirbazı'nı **Başlat'ı seçin.**

3. Profil **oluşturma yöntemi olarak** Ölçümler'i seçin ve ardından Sonraki'ye **tıklayın.**

4. Profili **oluşturmak istediğiniz aşağıdaki kullanılabilir hedeflerden hangisidir?** içinde öğesinin adını seçin. *dll projesine* tıklayın ve ardından Sonraki **'ye tıklayın.**

5. Sihirbazdan çıkmak için Son'a tıklayın ve yeni performans oturumunu **Performans Gezgini** açın. 

6. Hedefler'e **sağ tıklayın ve** hedef **ekle'yi Project.**

7. Hedef **Ekle Project** listesinden, DLL'yi alıştırmak için kullanmak istediğiniz yürütülebilir projeyi seçin.

     İsteğe bağlı. Profili oluşturmak istediğiniz dll projelerini ekebilirsiniz.

8. Eklenen bir proje için veri toplamayı önlemek için projenin adına sağ tıklayın ve ardından Ölçüm kutusu **işaretini** kaldırın.

## <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Profilde bağımsız ikili dosyalar olarak belirli DLL'ler belirtmek için

1. Visual Studio'yu açın.

2. Analiz menüsünde **Performans** Sihirbazı'nı **Başlat'ı seçin.**

3. Aşağıdaki **kullanılabilir hedeflerden hangilerinin** profilini oluşturmak istediğinizi seçin, Dinamik bağlantı kitaplığı profili **(.DLL)** seçin ve ardından Sonraki 'ye **tıklayın.**

4. Sihirbazın ikinci sayfasında aşağıdaki adımları gerçekleştirin:

    - yolunu ve dosya adını yazın. *Dll* yolunda profilini oluşturmak istediğiniz **dll dosyası.** Ayrıca, dosyayı Profil için Dinamik bağlantı kitaplığı iletişim kutusunda bulmak için üç nokta düğmesine (...) **tıklayabilirsiniz.** kopyasını belirtmeniz gerektiğini unutmayın. *yürütülebilir* dosyası tarafından başlatacak dll dosyası ( .*exe*) dosyasını seçin.

    - Yürütülebilir dosyanın yolunu ve dosya adını yazın (.*exe*) dosyasını kullanın. *yürütülebilir* **yolunda** dll. Ayrıca, başlatmak üzere Yürütülebilir iletişim kutusunda dosyayı bulmak için üç nokta düğmesine (...) **tıklayabilirsiniz.**

    - İsteğe bağlı. Komut satırı bağımsız değişkenleri'ne yürütülebilir dosyaya geçmek istediğiniz komut satırı **bağımsız değişkenlerini yazın.** Gerekirse, çalışma dizininde uygulamanın çalışma **dizinini belirtin.**

    - **İleri**’ye tıklayın.

5. Profil **oluşturma yöntemi olarak** Ölçümler'i seçin ve ardından Sonraki'ye **tıklayın.**

6. Sihirbazdan çıkmak için Son'a tıklayın ve yeni performans oturumunu **Performans Gezgini** açın. 

7. İsteğe bağlı. Daha fazla eklemek için. *dll* dosyalarında Hedefler'e **sağ tıklayın ve hedef** ikili dosya **ekle'yi seçin.** Hedef İkili Ekle iletişim **kutusundan dosyaları** seçin.

    > [!NOTE]
    > Yürütülebilir dosyayı () belirtme.*EXE*) dosyasını kullanın.

## <a name="see-also"></a>Ayrıca bkz.

[Veri toplamayı denetleme](../profiling/controlling-data-collection.md) 
 [Nasıl kullanılır: Araçları belirli işlevlerle sınırlama](../profiling/how-to-limit-instrumentation-to-specific-functions.md)
