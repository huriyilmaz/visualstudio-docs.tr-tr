---
title: "Nasıl yapılır: belirli dll 'Lerle Izleme sınırlandırma | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, runtime profiling control window
ms.assetid: 17c5996f-e3d0-4e44-b175-52b401b0f2d5
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5dc2fe8e6f9b0ed1e6970943ab5eedf1b62eb961
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64807728"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>Nasıl yapılır: Belirli DLL'ler için Araçları Sınırlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İzleme profili oluşturma yöntemini kullanarak, bir uygulamadaki bir veya daha fazla dll ile profil oluşturma verilerinin toplanmasını sınırlayabilirsiniz. Bir uygulamadaki bir veya daha fazla dll profilini oluşturmak için, hedef olarak. dll dosyalarını içeren bir performans oturumu oluşturursunuz. Profil eklemek istediğiniz dll 'Leri bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözümde veya bağımsız ikili dosyalarda projeler olarak belirtebilirsiniz.  
  
### <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Bir Visual Studio çözümünde belirli dll 'Leri izleme ile sınırlamak için  
  
1. İçindeki DLL dosyasını içeren çözümü açın [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] .  
  
2. **Çözümle** menüsünde, **Performans Sihirbazını Başlat**' ı seçin.  
  
3. Profil oluşturma yöntemi olarak **Araçlar** ' ı seçin ve ardından **İleri**' ye tıklayın.  
  
4. **Aşağıdaki kullanılabilir hedeflerden hangisi profilini oluşturmak istersiniz?**,. dll projesinin adını seçin ve ardından **İleri**' ye tıklayın.  
  
5. Sihirbazdan çıkmak için **son** ' a tıklayın ve yeni performans oturumunu **Performans Gezgini** penceresinde görüntüleyin.  
  
6. **Hedefler** ' e sağ tıklayın ve ardından **hedef proje Ekle**' yi seçin.  
  
7. **Hedef proje Ekle** LISTESINDEN, dll 'yi kullanmak için kullanmak istediğiniz çalıştırılabilir projeyi seçin.  
  
     İsteğe bağlı. Profil eklemek istediğiniz herhangi bir DLL projesini ekleyebilirsiniz.  
  
8. Eklenen bir proje için veri toplamayı engellemek için, projenin adına sağ tıklayın ve ardından **gereç** onay kutusunu temizleyin.  
  
### <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>Belirli dll 'Lerin bağımsız ikili dosyalar olarak profilini belirtmek için  
  
1. [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] dosyasını açın.  
  
2. **Çözümle** menüsünde, **Performans Sihirbazını Başlat**' ı seçin.  
  
3. **Aşağıdaki kullanılabilir hedeflerden hangisi profilini oluşturmak**istersiniz, **bir dinamik bağlantı kitaplığı profili seçin (. DLL)** ve ardından **İleri**' ye tıklayın.  
  
4. Sihirbazın ikinci sayfasında, aşağıdaki adımları uygulayın:  
  
    - **DLL yolunda**profil eklemek istediğiniz. dll dosyasının yolunu ve dosya adını yazın. Ayrıca, dosyayı **profile olan dinamik bağlantı kitaplığı** iletişim kutusunda bulmak için üç nokta düğmesini (...) de tıklayabilirsiniz. İleri ' yi seçtiğiniz yürütülebilir (. exe) dosya tarafından başlatılacak. dll dosyasının kopyasını belirtmeniz gerektiğini unutmayın.  
  
    - **Yürütülebilir yolda**. dll ' yi çalışacak yürütülebilir (. exe) dosyanın yolunu ve dosya adını yazın. Ayrıca, **başlatılacak yürütülebilir** iletişim kutusunda dosyayı bulmak için üç nokta düğmesini (...) de tıklayabilirsiniz.  
  
    - İsteğe bağlı. **Komut satırı bağımsız değişkenlerinde**yürütülebilir dosyaya geçirmek istediğiniz komut satırı bağımsız değişkenlerini yazın. Gerekirse, **çalışma dizinindeki**uygulama için çalışma dizinini belirtin.  
  
    - **İleri**’ye tıklayın.  
  
5. Profil oluşturma yöntemi olarak **Araçlar** ' ı seçin ve ardından **İleri**' ye tıklayın.  
  
6. Sihirbazdan çıkmak için **son** ' a tıklayın ve yeni performans oturumunu **Performans Gezgini** penceresinde görüntüleyin.  
  
7. İsteğe bağlı. Daha fazla. dll dosyası eklemek için **hedefler** ' e sağ tıklayın ve ardından **hedef ikilisi Ekle**' yi seçin. **Hedef Ikili Ekle** iletişim kutusundan dosyaları seçin.  
  
    > [!NOTE]
    > Dll 'Leri uygulayan yürütülebilir (. exe) dosyayı belirtmeyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri toplamayı denetleme](../profiling/controlling-data-collection.md)   
 [Nasıl yapılır: Belirli İşlevler için Araçları Sınırlama](../profiling/how-to-limit-instrumentation-to-specific-functions.md)
