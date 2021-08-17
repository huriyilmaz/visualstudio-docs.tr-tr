---
title: UWP uygulamaları için Birim Testleri Oluşturma ve Çalıştırma
description: Evrensel Visual Studio Platform uygulamaları için birim testi desteği Windows öğrenin. Visual Studio C#, Visual Basic ve C++ için birim testi şablonları sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 91efcd80f1f805e4b841d5abf68082c718ef93cacc2bfb21ed323513b4044a7e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424771"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>İzlenecek yol: UWP uygulamaları için birim testleri oluşturma ve çalıştırma

Visual Studio, Universal Windows Platform (UWP) uygulamaları için birim testi desteği içerir. Visual Studio C#, Visual Basic ve C++ için birim testi proje şablonları sağlar.

> [!TIP]
> UWP uygulamaları geliştirme hakkında daha fazla bilgi için [bkz. UWP uygulamalarını kullanma.](/windows/uwp/get-started/)

Aşağıdaki yordamlar, UWP uygulaması için birim testlerini oluşturma, çalıştırma ve hata ayıklama adımlarını açıklar.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>UWP uygulaması için birim testi projesi oluşturma

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

2. Yeni proje oluştur sayfasının **arama kutusuna** birim testi **girin.**

   Şablon listesi, birim testi için filtrelerini içerir.

3. C# veya Visual Basic için Birim Testi Uygulaması **(Evrensel Windows)** şablonunu seçin ve ardından Sonraki 'yi **seçin.**

   ![Visual Studio'de yeni UWP birim testi uygulaması oluşturma](media/vs-2019/new-uwp-unit-test-app.png)

4. İsteğe bağlı olarak proje veya çözüm adını ve konumunu değiştirerek Oluştur'a **seçin.**

5. İsteğe bağlı olarak hedef ve en düşük platform sürümlerini değiştirerek Tamam'ı **seçin.**

Bu adımları tamamladıktan sonra birim testi projesi oluşturulur ve proje Çözüm Gezgini.

![Çözüm Gezgini'de UWP birim testi Çözüm Gezgini](media/vs-2019/uwp-unit-test-project-solution-explorer.png)

::: moniker-end

::: moniker range="vs-2017"

1. Dosya **menüsünden** Yeni **dosya'Project.**

   Yeni **Project** iletişim kutusu görüntülenir.

2. Şablonlar'ın altında birim testleri oluşturmak istediğiniz programlama dilini seçin ve ardından Evrensel birim testi Windows ilişkili dili seçin. Örneğin, **Visual C# 'yi** ve ardından Windows'ı seçin ve ardından Birim Testi Kitaplığı  **(Evrensel Windows) seçin.**

3. (İsteğe bağlı) Ad **metin** kutusuna proje için kullanmak istediğiniz adı girin.

4. (İsteğe bağlı) Projeyi oluşturmak istediğiniz yolu, Konum metin kutusuna girerek  veya Gözat düğmesini **seçerek** değiştirebilirsiniz.

5. (İsteğe bağlı) Çözüm **adı** metin kutusuna çözümünüz için kullanmak istediğiniz adı girin.

6. Çözüm için **dizin oluştur seçeneğini seçili** bırakın ve Tamam **düğmesini** seçin.

   ![Uyarlanmış Birim Testi Kitaplığı](../test/media/unit_test_win8_1.png)

   **Çözüm Gezgini** UWP birim testi projesiyle doldurulur ve kod düzenleyicisi UnitTest1 başlıklı varsayılan birim testini görüntüler.

   ![Yeni uyarlanmış birim testi projesi](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

::: moniker-end

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Birim testi projesinin UWP uygulama bildirim dosyasını düzenleme

1. Uygulama **Çözüm Gezgini** *Package.appxmanifest* dosyasına sağ tıklayın ve Aç'ı **seçin.**

2. Bildirim **Tasarımcısı'nda** Özellikler **sekmesini** seçin.

3. Özellikler altındaki **listede,** birim teste ihtiyacınız olan özellikleri ve test etmek için kod seçin. Örneğin, birim **testinin ve** test kodunun İnternet'e erişim yeteneğine sahip olması gerekirse İnternet onay kutusunu seçin.

   > [!NOTE]
   > Seçen özellikler yalnızca birim testinin düzgün çalışması için gereken özellikleri içermesi gerekir.

   ![Birim Testi Bildirimi](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>UWP uygulaması için birim testini kodla

Kod düzenleyicisinde birim testini düzenleyin ve test için gereken onayları ve mantığı ekleyin.

## <a name="run-unit-tests"></a>Birim testlerini çalıştırma

Çözümü derlemek ve Test Gezgini'ni kullanarak birim testini çalıştırmak için:

1. Test **menüsünde,** **Windows'ı ve** ardından **Test Gezgini'ni seçin.**

2. Derleme **menüsünden** Çözümü **Derleme'yi seçin.**

   Birim testini şimdi Test Gezgini'nde gösterebilirsiniz.

   > [!NOTE]
   > Test Gezgini'nde birim testleri listesini güncelleştirmek için çözümü derlemeniz gerekir.

3. **Test Gezgini'nde,** oluşturduğunuz birim testini seçin.

4. Hepsini **Çalıştır'ı seçin.**

   ![Birim Testi Gezgini &#45; testi çalıştırma](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

   > [!TIP]
   > Test Gezgini'nde listelenen bir veya daha fazla birim testini seçebilir ve ardından sağ tıklar ve Seçili Testleri **Çalıştır'ı seçebilirsiniz.**
   >
   > Ayrıca, Seçili Testlerde **Hata Ayıklamayı, Testi** **Aç'ı seçebilir** ve Özellikler seçeneğini **kullanabilirsiniz.**
   >
   > ![Birim Testi Gezgini &#45; birim testi bağlam menüsü](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

   Birim testi çalışır. Tamamlandıktan sonra, Test Gezgini test durumunu ve geçen zamanı görüntüler ve kaynağın bağlantısını sağlar.

   ![Birim Testi Gezgini &#45; testi tamamlandı](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Ayrıca bkz.

- [UWP uygulamalarını Visual Studio](../test/unit-test-your-code.md)
- [UWP uygulaması oluşturma ve test edin](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)
