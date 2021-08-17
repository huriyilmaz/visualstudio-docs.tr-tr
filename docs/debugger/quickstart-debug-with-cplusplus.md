---
title: C++ hata ayıklama
description: Visual Studio hata ayıklayıcısını kullanarak yerel Visual Studio ayıklama
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: 639e430b-6d2d-46bd-b738-8c60dfb384f1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: 0292e73f952a05652142b8e146d21915af73bde2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105034"
---
# <a name="quickstart-debug-with-c-using-the-visual-studio-debugger"></a>Hızlı Başlangıç: Visual Studio hata ayıklayıcısını kullanarak C++ ile hata ayıklama

Hata Visual Studio hata ayıklayıcısı, uygulamalarınızı hata ayıklamanıza yardımcı olacak birçok güçlü özellik sağlar. Bu konu, temel özelliklerden bazıları hakkında bilgi edinmek için hızlı bir yol sağlar.

## <a name="create-a-new-project"></a>Yeni proje oluşturma

1. Visual Studio açın ve proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama **kutusunu açmak için Ctrl + Q** yazın, **c++** yazın, Şablonlar'ı seçin ve ardından Yeni Konsol Uygulaması projesi **oluştur'a tıklayın.**  Görüntülenen iletişim kutusunda Oluştur'a **tıklayın.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **dosya'Project.**  >    >   Yeni proje iletişim  kutusunun sol bölmesinde, **Visual C++** altında Windows **Masaüstü'ne** tıklayın ve orta bölmede Konsol **Uygulaması'Windows seçin.** Ardından **MyDbgApp** gibi bir ad yazın ve Tamam'a **tıklayın.**
    ::: moniker-end

    **Windows** Konsol Uygulaması proje şablonunu görmüyorsanız Araçlar Araçları ve Özellikleri Al... 'a gidin  >  **ve** Visual Studio Yükleyicisi. Uygulama Visual Studio Yükleyicisi başlatıyor. **C++ ile masaüstü geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

    Visual Studio projeyi oluşturur.

1. MyDbgApp.cpp içinde aşağıdaki kodu değiştirin

    ```c++
    int main()
    {
        return 0;
    }
    ```

    bu kodla (kaldırmayın): `#include "stdafx.h"`

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

Kesme *noktası,* değişkenlerin değerlerine Visual Studio veya bellek davranışına veya bir kod dalını çalıştırıp çalıştırmamaya bakabilirsiniz. Hata ayıklamanın en temel özelliğidir.

1. Kesme noktası ayarlamak için işlev çağrısının sol tarafından sol tarafta yer alan oluklara tıklayın (veya kod satırına tıklayın ve `doWork` **F9 tuşuna basın).**

    ![Kesme noktası ayarlama](../debugger/media/dbg-qs-set-breakpoint.png "Kesme noktası ayarlama")

2. Şimdi **F5 tuşuna basın** (veya Hata **Ayıkla'> Hata Ayıklamayı Başlat'ı seçin).**

    ![Kesme noktası isabeti](../debugger/media/dbg-qs-hit-breakpoint.png "Kesme noktası isabeti")

    Hata ayıklayıcısı kesme noktası ayarlayıcıyı duraklatıyor. Hata ayıklayıcısı ve uygulama yürütmenin duraklatılmış olduğu deyim sarı okla işaret ediyor. İşlev çağrısına `doWork` sahip satır henüz yürütülmedi.

    > [!TIP]
    > Döngüde veya recursion içinde bir kesme noktanız varsa veya sık sık adım attığınız [](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) çok sayıda kesme noktanız varsa, kodunuzun YALNIZCA belirli koşullar karşılandı olduğunda askıya alındıktan emin olmak için koşullu kesme noktası kullanın. Koşullu kesme noktası zamandan tasarruf sağlar ve yeniden oluşturması zor olan sorunlarda hata ayıklamayı da kolaylaştırır.

    C++ içinde bellekle ilgili hatalarda hata ayıklamaya çalışırken, adres değerlerini (NULL ara) ve başvuru sayılarını incelemek için kesme noktaları da kullanabilirsiniz.

## <a name="navigate-code"></a>Kodda gezinme

Hata ayıklayıcıya devam etme talimatı için farklı komutlar vardır. 2017'den itibaren kullanılabilen yararlı bir kod gezinti Visual Studio gösteriyoruz.

Kesme noktası duraklatılırken, yeşil Renkli Çalıştır düğmesine tıklar görünene kadar deyimin üzerine gelin ve ardından `c1.push_back(20)` **Çalıştır'a tıklayarak düğmesine** basın.  ![](../debugger/media/dbg-tour-run-to-click.png "RunToClick")

![Tıklamak için çalıştır](../debugger/media/dbg-qs-run-to-click.png "Tıklamak için çalıştır")

Uygulama, çağrısıyla `doWork` yürütmeye devam eder ve düğmesine tıklamış kod satırı üzerinde duraklatılır.

Kodda adım adım gezinmek için kullanılan yaygın klavye komutları **F10** ve **F11'tir.** Daha ayrıntılı yönergeler için bkz. [Hata ayıklayıcıya ilk bakış.](../debugger/debugger-feature-tour.md)

## <a name="inspect-variables-in-a-datatip"></a>Veri ipucunda değişkenleri inceleme

1. Geçerli kod satırı (sarı yürütme işaretçisi ile işaretlenmiş) farenizin olduğu nesnenin üzerine gelerek `c1` bir veri ipucu gösterir.

    ![Veri ipucu görüntüleme](../debugger/media/dbg-qs-data-tip.png "Veri ipucu görüntüleme")

    Veri ipucu değişkenin geçerli değerini `c1` gösterir ve özelliklerini incelemeye olanak sağlar. Hata ayıklama sırasında, beklemeyebilirsiniz bir değer görüyorsanız, büyük olasılıkla önceki veya çağıran kod satırlarında bir hata vardır.

2. Nesnenin geçerli özellik değerlerine bakmak için veri ipucuna `c1` bakın.

3. Kod yürütürken değerini görmeye devam etmek için veri ipucuna sabitlemek için küçük pin `c1` simgesine tıklayın. (Sabitlenmiş veri ipucunı uygun bir konuma taşıyabilirsiniz.)

## <a name="edit-code-and-continue-debugging"></a>Kodu düzenleme ve hata ayıklamaya devam etme

Hata ayıklama oturumunun ortasındayken kodunda test etmek istediğiniz bir değişikliği tespit ediyorsanız, bunu da kullanabilirsiniz.

1. İkinci örneğine tıklayın `c2.front()` ve olarak `c2.front()` `c2.back()` değişir.

2. Hata ayıklayıcıyı ilerlemek **ve düzenlenen kodu yürütmek için** birkaç kez **F10** 'a (veya Hata Ayıkla > AdımLa) tuşuna basın.

    ![Düzenle ve devam](../debugger/media/dbg-qs-edit-and-continue.gif "Düzenle ve devam")

    **F10,** hata ayıklayıcıyı tek tek bir deyime ilerletmektedir, ancak işlevlere adımlarını atlar (atlayıp atlayılan kod yine de yürütülür).

Düzenle ve devam edin özelliğini kullanma ve özellik sınırlamaları hakkında daha fazla bilgi için bkz. Düzenle [ve Devam Edin.](../debugger/edit-and-continue.md)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide hata ayıklayıcıyı başlatmayı, kodu adım adım incelemeyi ve değişkenleri incelemeyi öğrendiniz. Daha fazla bilgi için bağlantılarla birlikte hata ayıklayıcı özelliklerine üst düzey bir bakış elde etmek iyi olabilir.

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
