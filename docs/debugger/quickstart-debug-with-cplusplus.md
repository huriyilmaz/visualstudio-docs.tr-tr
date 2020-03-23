---
title: Hata Ayıklama C++
description: Visual Studio hata ayıklayıcısını kullanarak yerel kodu hata ayıklama
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: b619b2b6c93da8be399b2fc35d81ffe226f408ad
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "65679410"
---
# <a name="quickstart-debug-with-c-using-the-visual-studio-debugger"></a>Quickstart: Visual Studio hata ayıklama kullanarak C++ ile hata ayıklama

Visual Studio hata ayıklama, uygulamalarınızı hata ayıklamanıza yardımcı olacak birçok güçlü özellik sağlar. Bu konu, bazı temel özellikleri öğrenmek için hızlı bir yol sağlar.

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma

1. Visual Studio'u açın ve bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama kutusunu açmak için **Ctrl + Q** yazın, **c++** yazın, **Şablonlar'ı**seçin, ardından **yeni Konsol Uygulaması projesi oluştur'u**seçin. Görünen iletişim kutusunda **Oluştur'u**seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **Visual C++** altında, **Windows Desktop'ı**seçin ve sonra orta bölmede Windows **Console Uygulamasını**seçin. Ardından, **MyDbgApp** gibi bir ad yazın ve **Tamam'ı**tıklatın.
    ::: moniker-end

    **Windows Console Application** proje şablonu görmüyorsanız, Visual Studio Yükleyici'yi açan **Araçlar** > **Araçları ve Özellikleri Al...**(Visual Studio Installer'ı açar) gidin. Visual Studio Installer başlattı. C++ iş **yüküyle Masaüstü geliştirmeyi** seçin ve ardından **Değiştir'i**seçin.

    Visual Studio projeyi oluşturur.

1. MyDbgApp.cpp'de aşağıdaki kodu değiştirin

    ```c++
    int main()
    {
        return 0;
    }
    ```

    bu kod ile (kaldırmayın): `#include "stdafx.h"`

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

*Kesme noktası,* Visual Studio'nun çalışan kodunuzu nerede askıya alması gerektiğini gösteren bir işaretçidir, böylece değişkenlerin değerlerine veya belleğin davranışına veya bir kod dalının çalıştırılıp çalıştırılmayacağına göz atabilirsiniz. Hata ayıklamanın en temel özelliğidir.

1. Kesme noktasını ayarlamak `doWork` için, işlev çağrısının solundaki olukta tıklayın (veya kod çizgisini seçin ve **F9**tuşuna basın).

    ![Kesme noktası ayarlama](../debugger/media/dbg-qs-set-breakpoint.png "Kesme noktası ayarlama")

2. Şimdi **F5** tuşuna basın (veya **Hata Ayıklama > Hata Ayıklama'yı başlat'ı**seçin).

    ![Bir kesme noktasına çarptım](../debugger/media/dbg-qs-hit-breakpoint.png "Bir kesme noktasına çarptım")

    Hata ayıklama, kesme noktasını ayarladığınız yerde duraklar. Hata ayıklama ve uygulama yürütmenin duraklattığı deyim sarı okla gösterilir. İşlev çağrısıyla `doWork` gelen satır henüz yürütülmedi.

    > [!TIP]
    > Bir döngü veya özyinelemede bir kesme noktanız varsa veya sık sık adım attığınız çok sayıda kesme noktanız varsa, yalnızca belirli koşullar karşılandığında kodunuzun askıya aldığından emin olmak için [koşullu](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) bir kesme noktası kullanın. Koşullu bir kesme noktası zamandan tasarruf sağlar ve yeniden oluşturulması zor olan sorunları ayıklamayı da kolaylaştırabilir.

    C++'da bellekle ilgili hataları ayıklamaya çalışırken, adres değerlerini (NULL'u aramak) ve başvuru sayılarını incelemek için kesme noktalarını da kullanabilirsiniz.

## <a name="navigate-code"></a>Kodda gezinme

Hata ayıkıcıya devam etmesini emretmek için farklı komutlar vardır. Visual Studio 2017'den itibaren kullanılabilen kullanışlı bir kod navigasyon komutu gösteriyoruz.

Kesme noktasında duraklatılırken, yeşil `c1.push_back(20)` **Çalıştır'dan Tıklatdüğmesine tıklayın** düğmesine kadar deyimin üzerine basın ve ardından ![Run to Click](../debugger/media/dbg-tour-run-to-click.png "RunToClick") **Tıklatmak için Çalıştır düğmesine basın.**

![Tıklatmak için çalıştırın](../debugger/media/dbg-qs-run-to-click.png "Tıklatmak için çalıştırın")

Uygulama yürütmeye devam `doWork`eder, arama ve düğmeyi tıklattığınızda kod satırında duraklar.

Koda basmak için kullanılan yaygın klavye komutları **F10** ve **F11'i**içerir. Daha ayrıntılı talimatlar için [hata ayıklama bölümüne ilk bakışta](../debugger/debugger-feature-tour.md)bakın.

## <a name="inspect-variables-in-a-datatip"></a>Veri ucundaki değişkenleri inceleyin

1. Geçerli kod satırında (sarı yürütme işaretçisi ile `c1` işaretlenmiş), bir veri ipucu göstermek için fareniz ile nesnenin üzerine gelin.

    ![Veri ipucunu görüntüleme](../debugger/media/dbg-qs-data-tip.png "Veri ipucunu görüntüleme")

    Veri ipucu, `c1` değişkenin geçerli değerini gösterir ve değişkenin özelliklerini incelemenize olanak tanır. Hata ayıklama yaparken, beklemediğiniz bir değer görürseniz, büyük olasılıkla önceki veya kod satırlarını çağıran bir hatanız vardır.

2. Nesnenin geçerli özellik değerlerine bakmak için `c1` veri ucunu genişletin.

3. Kod `c1` yürütürken değerini görmeye devam etmek için veri ucunu sabitlemek istiyorsanız, küçük pin simgesini tıklatın. (Sabitlenmiş veri ucunu uygun bir konuma taşıyabilirsiniz.)

## <a name="edit-code-and-continue-debugging"></a>Kodu düzenleme ve hata ayıklamaya devam etme

Hata ayıklama oturumunun ortasındayken kodunuzda sınamak istediğiniz bir değişikliği tanımlarsanız, bunu da yapabilirsiniz.

1. İkinci örneğini `c2.front()` tıklatın `c2.front()` ve `c2.back()`'' olarak değiştirin

2. Hata ayıklayıcıyı ilerletmek ve düzenlenen kodu yürütmek için **F10** (veya **Hata Ayıklama > Adım At)** tuşuna birkaç kez basın.

    ![Edin ve devam edin](../debugger/media/dbg-qs-edit-and-continue.gif "Edin ve devam edin")

    **F10** hata ayıklayıcıyı bir defada bir ifadeyi ilerletir, ancak bunlara adım atmak yerine işlevlerin üzerine adım atar (atladığınız kod hala yürütülür).

Edit-and-continue ve özellik sınırlamaları hakkında daha fazla bilgi için [bkz.](../debugger/edit-and-continue.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, hata ayıklayıcıyı başlatmayı, koda nasıl basabileceğinizi ve değişkenleri nasıl inceleyincenizi öğrendiniz. Hata ayıklama özelliklerine daha fazla bilgi bağlantılarıyla birlikte üst düzey bir görünüm elde etmek isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
