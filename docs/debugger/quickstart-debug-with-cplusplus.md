---
title: Hata ayıklama C++
description: Visual Studio hata ayıklayıcısını kullanarak yerel kodda hata ayıklama
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 8735ecd409eca2801b42b11bd3928a00e5191bf8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840905"
---
# <a name="quickstart-debug-with-c-using-the-visual-studio-debugger"></a>Hızlı başlangıç: Visual Studio hata ayıklayıcısını kullanarak C++ ile hata ayıklama

Visual Studio hata ayıklayıcı, uygulamalarınızda hata ayıklamanıza yardımcı olmak için birçok güçlü özellik sunar. Bu konu, temel özelliklerden bazılarını öğrenmenin hızlı bir yolunu sağlar.

## <a name="create-a-new-project"></a>Yeni proje oluşturma

1. Visual Studio 'Yu açın ve bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **C++** yazın, **Şablonlar**' ı seçin ve **Yeni konsol uygulaması projesi oluştur**' u seçin. Görüntülenen iletişim kutusunda **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **Dosya**  >  **Yeni**  >  **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **Visual C++** altında, **Windows Masaüstü**' nün ardından orta bölmedeki **Windows konsol uygulaması**' nı seçin. Ardından, **Mydbgapp** gibi bir ad yazın ve **Tamam**' a tıklayın.
    ::: moniker-end

    **Windows konsol uygulaması** proje şablonunu görmüyorsanız, **Araçlar**  >  **ve Özellikler al.**.. ' a giderek Visual Studio yükleyicisi açılır. Visual Studio Yükleyicisi başlatılır. C++ iş yükü **Ile masaüstü geliştirmeyi** seçin ve ardından **Değiştir**' i seçin.

    Visual Studio projeyi oluşturur.

1. MyDbgApp. cpp içinde aşağıdaki kodu değiştirin

    ```c++
    int main()
    {
        return 0;
    }
    ```

    Bu kodla (kaldırmayın `#include "stdafx.h"` ):

    ```c++
    #include <list>
    #include <iostream>

    using namespace std;

    void doWork()
    {
        list <int> c1;

        c1.push_back(10);
        c1.push_back(20);

        const list <int> c2 = c1;
        const int &i = c2.front();
        const int &j = c2.front();
        cout << "The first element is " << i << endl;
        cout << "The second element is " << j << endl;

    }

    int main()
    {
        doWork();
    }
    ```

## <a name="set-a-breakpoint"></a>Kesme noktası ayarlama

*Kesme noktası* , Visual Studio 'nun çalışan kodunuzu askıya alması gerektiğini belirten bir işaretleyicidir, böylece değişkenlerin değerlerine veya bellek davranışına veya kodun bir dalının çalıştırılıp çalıştırılmayacağı konusunda bir görünüm elde edebilirsiniz. Hata ayıklamada en temel özelliktir.

1. Kesme noktasını ayarlamak için, işlev çağrısının solundaki cilt payın içine tıklayın `doWork` (veya kod satırını seçip **F9** tuşuna basın).

    ![Kesme noktası ayarlama](../debugger/media/dbg-qs-set-breakpoint.png "Kesme noktası ayarlama")

2. Şimdi **F5** tuşuna basın (veya hata **ayıklamayı başlatmak > hata ayıkla** seçeneğini belirleyin).

    ![Kesme noktasına isabet edin](../debugger/media/dbg-qs-hit-breakpoint.png "Kesme noktasına isabet edin")

    Hata ayıklayıcı, kesme noktasını ayarladığınız yerde duraklatılır. Hata ayıklayıcının ve uygulama yürütmenin duraklatıldığı ifade sarı oklu belirtilir. İşlev çağrısının bulunduğu satır `doWork` henüz yürütülmedi.

    > [!TIP]
    > Bir döngüde veya özyinelemedeki bir kesme noktası varsa veya sık sık adımtığınız çok sayıda kesme noktasına sahipseniz, kodunuzun yalnızca belirli koşullar karşılandığında askıya alındığından emin olmak için [koşullu bir kesme noktası](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) kullanın. Koşullu kesme noktası zaman kazandırır ve yeniden oluşturulması zor olan sorunların hatalarını ayıklamanızı kolaylaştırır.

    C++ ' da bellekle ilgili hatalarda hata ayıklamaya çalışırken, adres değerlerini incelemek için kesme noktaları da kullanabilirsiniz (NULL için arama) ve başvuru sayıları.

## <a name="navigate-code"></a>Koda git

Hata ayıklayıcının devam etmesini bildirmek için farklı komutlar vardır. Visual Studio 2017 ' den başlayarak kullanılabilecek yararlı bir kod Gezinti komutu gösteririz.

Kesme noktasında duraklalarken, tıklama `c1.push_back(20)` düğmesine tıklayarak ve ardından tıklama düğmesine tıklayarak  deyimin üzerine gelin ve ![](../debugger/media/dbg-tour-run-to-click.png "RunToClick") sonra da **Çalıştır** düğmesine basın.

![Tıklama için Çalıştır](../debugger/media/dbg-qs-run-to-click.png "Tıklama için Çalıştır")

Uygulama, `doWork` düğmeye tıklamış olduğunuz kod satırında yürütme, çağırma ve duraklamaya devam eder.

Kod içinde ilerlemek için kullanılan yaygın klavye komutları **F10** ve **F11**. Daha ayrıntılı yönergeler için bkz. [hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md).

## <a name="inspect-variables-in-a-datatip"></a>Bir veri ipucunda değişkenleri İnceleme

1. Geçerli kod satırında (Sarı yürütme işaretçisi tarafından işaretlenir), `c1` bir DataTip göstermek için farenizle nesnenin üzerine gelin.

    ![Veri ipucunu görüntüleme](../debugger/media/dbg-qs-data-tip.png "Veri ipucunu görüntüleme")

    Datatıp, değişkenin geçerli değerini gösterir `c1` ve özelliklerini incelemenizi sağlar. Hata ayıklarken, beklemediğinizi bir değer görürseniz, büyük olasılıkla kodun önceki veya çağırma satırlarında bir hata oluşur.

2. Nesnenin geçerli özellik değerlerini görmek için DataTip ' i genişletin `c1` .

3. Kodu yürüttüğünüzde değerini görmeye devam edebilmeniz için veri ipucunu sabitlemek istiyorsanız `c1` , küçük sabitle simgesine tıklayın. (Sabitlenmiş veri ipucunu uygun bir konuma taşıyabilirsiniz.)

## <a name="edit-code-and-continue-debugging"></a>Kodu düzenleme ve hata ayıklamaya devam etme

Hata ayıklama oturumunun ortasında kodunuzda test etmek istediğiniz bir değişikliği belirlerseniz, bunu da yapabilirsiniz.

1. İkinci örneğine tıklayın ve öğesini `c2.front()` olarak değiştirin `c2.front()` `c2.back()` .

2. Hata ayıklayıcıyı ilerletmek ve düzenlenmiş kodu yürütmek için **F10** 'e (veya **hata ayıklama > adımla**) birkaç kez basın.

    ![Düzenle ve devam et](../debugger/media/dbg-qs-edit-and-continue.gif "Düzenle ve devam et")

    **F10** , hata ayıklayıcı bir ifadeyi tek seferde ilerletir, ancak bunlar içine adımlamak yerine işlevler üzerinde adımlar (yine de atladığınız kod).

Düzenle ve devam et ve özellik sınırlamalarını kullanma hakkında daha fazla bilgi için bkz. [Düzenle ve devam et](../debugger/edit-and-continue.md).

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, hata ayıklayıcıyı başlatma, kod adım adım ve değişkenleri İnceleme hakkında öğrendiniz. Hata ayıklayıcı özelliklerine ve daha fazla bilgi için bağlantılarla birlikte yüksek düzeyde bir görünüm sağlamak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
