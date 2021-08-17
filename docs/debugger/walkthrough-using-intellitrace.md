---
title: IntelliTrace ile olayları | Microsoft Docs
description: Belirli olaylar, olay kategorileri ve tek tek işlev Visual Studio Enterprise verileri toplamak için IntelliTrace'i nasıl kullanabileceğiniz hakkında bilgi edinebilirsiniz.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ceb486aaa1564b9ee7a60cf7994fb849cf0f8260
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074117"
---
# <a name="view-events-with-intellitrace-in-visual-studio-enterprise-c-visual-basic"></a>IntelliTrace ile olayları Visual Studio Enterprise (C#, Visual Basic)

IntelliTrace'i kullanarak belirli olaylar veya olay kategorileri ya da olaylara ek olarak tek tek işlev çağrıları hakkında bilgi toplayabilirsiniz. Aşağıdaki yordamlarda bunun nasıl gerçekleştirl olduğu gösterildi.

IntelliTrace'i Visual Studio Enterprise veya Professional veya Community kullanabilirsiniz.

## <a name="configure-intellitrace"></a><a name="GettingStarted"></a> IntelliTrace'i yapılandırma

Yalnızca IntelliTrace olaylarıyla hata ayıklamayı denemeyi siniz. IntelliTrace olayları hata ayıklayıcı olayları, özel durumlar, .NET Framework olayları ve diğer sistem olaylarıdır. Hata ayıklamaya başlamadan önce IntelliTrace tarafından kaydedilen olayları kontrol etmek için belirli olayları açmalı veya kapatmanız gerekir. Daha fazla bilgi için bkz. [IntelliTrace Özellikleri.](../debugger/intellitrace-features.md)

- Dosya Erişimi için IntelliTrace olaylarını açın. **IntelliTrace > Için Araçlar > IntelliTrace >** sayfasına gidin ve Dosya **kategorisini** genişletin. Dosya olayı **kategorisini** kontrol edin. Bu, tüm dosya olaylarını (erişim, kapatma, silme) denetlenir.

## <a name="create-your-app"></a>Uygulama oluşturma

1. Bir C# konsol uygulaması oluşturun. Program.cs dosyasına aşağıdaki `using` deyimini ekleyin:

    ```csharp
    using System.IO;
    ```

2. Main <xref:System.IO.FileStream> yönteminde bir oluşturun, bu yöntemden okuyun, kapatın ve dosyayı silin. Yalnızca bir kesme noktası ayarlamak için başka bir satır ekleyin:

    ```csharp
    static void Main(string[] args)
    {
        FileStream fs = File.Create("WordSearchInputs.txt");
        fs.ReadByte();
        fs.Close();
        File.Delete("WordSearchInputs.txt");

        Console.WriteLine("done");
    }
    ```

3. Kesme noktası ayarlama `Console.WriteLine("done");`

## <a name="start-debugging-and-view-intellitrace-events"></a>Hata ayıklamayı başlatma ve IntelliTrace olaylarını görüntüleme

1. Her zamanki gibi hata ayıklamaya başlama. **(F5 tuşuna basın** veya **Hata Ayıklamayı Başlat >'a tıklayın.)**

    > [!TIP]
    > Bu **pencerelerde değerleri** **görmek ve** kaydetmek için hata ayıklarken Yereller ve Otomatikler pencerelerini açık tutma.

2. Yürütme kesme noktası sırasında durdurulur. Tanılama Araçları penceresini **görmüyorsanız** IntelliTrace Olayları'> Windows > **Ayıkla'ya tıklayın.**

    Tanılama Araçları **penceresinde** Olaylar sekmesini bulun  (Olaylar, Bellek Kullanımı ve CPU Kullanımı olmak için 3  **sekmeyi görüyor olun).** Olaylar **sekmesi,** hata ayıklayıcının yürütülmesini durdurmadan önceki son olayla biten olayların kronolojik bir listesini gösterir. Access WordSearchInputs.txtadlı **bir olay görüyor WordSearchInputs.txt.**

    Aşağıdaki ekran görüntüsü Visual Studio 2015 Güncelleştirme 1'den alındır.

    ![Visual Studio penceresinin ekran görüntüsü. Yürütme bir kesme noktası sırasında durdurulur ve Tanılama Araçları penceresindeki Olaylar sekmesi olayları listeler.](../debugger/media/intellitrace-update1.png)

3. Ayrıntılarını genişletmek için olayı seçin.

    Aşağıdaki ekran görüntüsü Visual Studio 2015 Güncelleştirme 1'den alındır.

    ![Visual Studio Tanılama Araçları penceresindeki Olaylar sekmesinin ekran görüntüsü. Bir olay seçilir ve ayrıntılarını gösterecek şekilde genişletilir.](../debugger/media/intellitraceupdate1-singleevent.png)

    Dosyayı açmak için pathname bağlantısını seçebilirsiniz. Tam yol adı kullanılamıyorsa Dosya **Aç iletişim** kutusu görüntülenir.

    Hata **ayıklayıcının** bağlamını, Çağrı **Yığını,** Yerel Ayarlar ve diğer katılan hata ayıklayıcı pencerelerinde  geçmiş verileri gösteren seçili olayın toplanmış olduğu zaman olarak ayarladığı Geçmiş Hata Ayıklamayı Etkinleştir'e tıklayın. Kaynak kodu varsa, Visual Studio, incelemeniz için işaretçiyi kaynak penceresinde ilgili koda taşır.

    Aşağıdaki ekran görüntüsü Visual Studio 2015 Güncelleştirme 1'den alındır.

    ![Visual Studio penceresinin ekran görüntüsü. Yürütme bir kesme noktası sırasında durdurulur, bir olay seçilir ve ilgili kod satırı vurgulanır.](../debugger/media/historicaldebugging-update1.png)

4. Hatayı bulamadıysanız, hataya neden olan diğer olayları incelemeyi deneyin. ayrıca intelliTrace kayıt çağrısı bilgilerine de sahip olabilir, böylece işlev çağrılarını adım adım takip edin.

## <a name="next-steps"></a>Sonraki Adımlar

Geçmiş hata ayıklama ile IntelliTrace'in gelişmiş özelliklerinden bazıları kullanabilirsiniz:

- Anlık görüntüleri görüntülemek için [bkz. IntelliTrace kullanarak önceki uygulama eyaletlerini inceleme](../debugger/view-historical-application-state.md)
- Değişkenleri incelemeyi ve kodda gezinmeyi öğrenmek için [bkz. Geçmiş hata ayıklama ile uygulamanızı inceleme](../debugger/historical-debugging-inspect-app.md)
