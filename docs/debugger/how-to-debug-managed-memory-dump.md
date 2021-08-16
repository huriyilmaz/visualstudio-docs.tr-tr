---
title: .NET tanılama Çözümleyicileri ile yönetilen bellek dökümünden hata ayıklama | Microsoft Docs
description: Visual Studio .net tanılama çözümleyicileri 'ni kullanarak yönetilen bellek dökümünü nasıl analiz edeceğinizi öğrenin
ms.custom: SEO-VS-2021
ms.date: 04/21/2021
ms.topic: how-to
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- analyzers
- dump debugging
- debugging managed memory dump
- debugging [Visual Studio]
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: a0931f6f8aba8dfbef705542cad889edc1441a327945d5640459e7cac4d0a2d5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379374"
---
# <a name="how-to-debug-a-managed-memory-dump-with-net-diagnostic-analyzers"></a>.NET tanılama Çözümleyicileri ile yönetilen bellek dökümünde hata ayıklama



Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Bellek dökümünü açma
> * Çözümleyicilere karşı çözümleyiciler seçme ve yürütme
> * Çözümleyicilerin sonuçlarını gözden geçirme
> * Sorunlu koda gitme


Bu makalede açıklanan örnekte, uygulamanız isteklerin zamanında yanıt vermemesine neden olabilir. 


## <a name="opening-a-memory-dump-in-visual-studio"></a>Visual Studio bir bellek dökümü açılıyor

1. **dosya > > dosya** menüsü komutunu açıp bellek dökümünü seçin Visual Studio bellek dökümünü açın.

1. Bellek dökümü Özeti sayfasında, **Tanılama analizini Çalıştır** adlı yeni bir **eylem** olduğuna dikkat edin.

   ![Eylem-tanılama Analizi](../debugger/media/diagnostic-analyzer-dump-summary-actions.png)

1. Hata ayıklayıcıyı başlatmak için bu eylemi seçin ve temel alınan belirtiyle düzenlenmiş kullanılabilir çözümleyici seçeneklerinin bir listesi ile yeni **Tanılama Analizi** sayfasını açın.


## <a name="select-and-execute-analyzers-against-the-dump"></a>Çözümleyicilere karşı çözümleyiciler seçme ve yürütme

Bu belirtileri araştırmak için en iyi seçenek, bu örnekteki sorunla en iyi şekilde eşleştiğinden, **Işlem yanıt verme** bölümünde bulunur.

   ![Tanılama Çözümleyicileri seçin](../debugger/media/diagnostic-analyzer-diagnostics-analysis-window.png)

1. Araştırma işlemini başlatmak için **Çözümle** düğmesine tıklayın 

1. Çözümleyici, bellek dökümünde yakalanan işlem bilgilerinin ve CLR verilerinin birleşimine bağlı olarak sonuçlara neden olur.
 
## <a name="review-the-results-of-the-analyzers"></a>Çözümleyicilerin sonuçlarını gözden geçirme

1. Bu durumda, çözümleyici iki hata buldu. **Analiz özetini** ve önerilen **düzeltmeyi** görmek için çözümleyici sonucunu seçin.

   ![Tanılama Çözümleyicileri sonuçları](../debugger/media/diagnostic-analyzer-diagnostics-analysis-results.png)

1. **Analiz Özeti** , "CLR iş parçacığı havuzu 'nun başlangıçlanmayı yaşadığını" ifade etti. Bu bilgiler, CLR 'nin şu anda kullanılabilir olan tüm iş parçacığı havuzu iş parçacıklarını kullanmışsa ve bu, hizmetinizin bir iş parçacığı yayımlanıncaya kadar yeni isteklere yanıt veremediği anlamına gelir.

    > [!NOTE] 
    > Bu durumda **Düzeltme** , "zaman uyumlu olarak Izleyici, olay, görev veya iş parçacığını engelleyebilen diğer nesneler üzerinde bekleme" olur. Yöntemi zaman uyumsuz olacak şekilde güncelleştirip Güncelleştir, bkz..

## <a name="navigating-to-the-problematic-code"></a>Sorunlu koda gitme

Sonraki işim sorunlu kodu bulmaktan sonra.

1. **çağrı yığınını göster** bağlantısına tıklanınca Visual Studio, bu davranışı gösteren iş parçacıklarına hemen geçer.

1. **Çağrı yığını** penceresinde, kod (SyncOverAsyncExmple.*) ile çerçeve kodundan (System.*) arasında hızlı bir şekilde ayırt edilebilen yöntemler gösterilir.

   ![Tanılama belirteçleri, çağrı yığınına bağlanır](../debugger/media/diagnostic-analyzer-call-stack.png)

1. her çağrı yığını çerçevesi bir yönteme karşılık gelir ve yığın çerçevelerine çift tıklanarak Visual Studio bu iş parçacığında doğrudan bu senaryoya işaret eden koda gidecektir.

1. Bu örnekte, bir sembol veya kod yoktur, ancak, **simge yüklü değil** sayfasında, **[kaynak kodunu derlemeyi kaldırma](../debugger/decompilation.md)** seçeneğini belirleyebilirsiniz.

   ![Ilspy](../debugger/media/diagnostic-analyzer-decompilation.png)

1. Aşağıdaki ayrıştırılmış kaynakta, zaman uyumsuz bir görevin (Tüketimethreadpoolthread) zaman uyumlu bir engelleme işlevini çağırıyor olması önerilir.

    > [!NOTE]  
    > Bir WaitHandle. WaitOne yöntemi içeren "Dosomeiz ()" yöntemi, bir sinyal alıncaya kadar geçerli iş parçacığı havuzu iş parçacığını engelliyor.

   Uygulamaların yanıt hızını artırmak için, tüm zaman uyumsuz bağlamlardan zaman uyumlu kod engellemeyi kaldırmak önemlidir.

   ![Ayrıştırılmış kodu analiz etme](../debugger/media/diagnostic-analyzer-decompiled-code.png)


## <a name="see-also"></a>Ayrıca bkz.

* [Hata ayıklayıcıda döküm dosyalarını kullanma](../debugger/using-dump-files.md)
* [Hata ayıklama sırasında .NET derlemelerinden kaynak kodu oluşturma](../debugger/decompilation.md)
* [Sembol (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
