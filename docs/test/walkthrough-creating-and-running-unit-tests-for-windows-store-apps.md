---
title: UWP uygulamaları için birim testleri oluşturma ve çalıştırma
description: Uygulamalar Evrensel Windows Platformu birim testi için Visual Studio desteği hakkında bilgi edinin. Visual Studio, C#, Visual Basic ve C++ için birim test şablonları sağlar.
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
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 52b7712c3e2e283dc92da3b920eccdcb0c312cd4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948042"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>İzlenecek yol: UWP uygulamaları için birim testleri oluşturma ve çalıştırma

Visual Studio, birim testi Evrensel Windows Platformu (UWP) uygulamaları için destek içerir. Visual Studio, C#, Visual Basic ve C++ için birim testi proje şablonları sağlar.

> [!TIP]
> UWP uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [UWP uygulamalarını kullanmaya](/windows/uwp/get-started/)başlama.

Aşağıdaki yordamlarda, UWP uygulaması için birim testleri oluşturma, çalıştırma ve hata ayıklama adımları açıklanır.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>UWP uygulaması için birim testi projesi oluşturma

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

2. **Yeni proje oluştur** sayfasının arama kutusunda **birim testi** girin.

   Şablon listesi, birim testi için olanlarla filtreler.

3. C# veya Visual Basic için **birim testi uygulaması (Evrensel Windows)** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Visual Studio 'da yeni UWP birim testi uygulaması oluşturma](media/vs-2019/new-uwp-unit-test-app.png)

4. İsteğe bağlı olarak proje veya çözüm adını ve konumunu değiştirip **Oluştur**' u seçin.

5. İsteğe bağlı olarak hedef ve en düşük platform sürümlerini değiştirip **Tamam**' ı seçin.

Bu adımları tamamladıktan sonra, birim test projesi oluşturulur ve Çözüm Gezgini içinde görüntülenir.

![Çözüm Gezgini UWP birim testi projesi](media/vs-2019/uwp-unit-test-project-solution-explorer.png)

::: moniker-end

::: moniker range="vs-2017"

1. **Dosya** menüsünden **Yeni proje**' yi seçin.

   **Yeni proje** iletişim kutusu görüntülenir.

2. Şablonlar ' ın altında, birim testleri oluşturmak istediğiniz programlama dilini seçin ve ardından ilişkili Windows Evrensel birim testi kitaplığını seçin. Örneğin, **Visual C#** ' yi ve ardından **Windows Universal**' i seçin ve ardından **birim testi kitaplığı (Evrensel Windows)** öğesini seçin.

3. Seçim **Ad** metin kutusuna, proje için kullanmak istediğiniz adı girin.

4. Seçim Projeyi, **konum** metin kutusuna girerek oluşturmak istediğiniz yolu değiştirin veya **Araştır** düğmesini seçin.

5. Seçim **Çözüm** adı metin kutusuna çözümünüz için kullanmak istediğiniz adı girin.

6. **Çözüm için dizin oluştur** seçeneğini seçili bırakın ve **Tamam** düğmesini seçin.

   ![Özel birim testi kitaplığı](../test/media/unit_test_win8_1.png)

   **Çözüm GEZGINI** UWP birim testi projesi ile doldurulur ve kod Düzenleyicisi UnitTest1 başlıklı varsayılan birim testini görüntüler.

   ![Yeni özel birim testi projesi](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

::: moniker-end

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Birim testi projesinin UWP uygulaması bildirim dosyasını Düzenle

1. **Çözüm Gezgini**, *Package. appxmanifest* dosyasına sağ tıklayın ve **Aç**' ı seçin.

2. **Bildirim tasarımcısında** **yetenekler** sekmesini seçin.

3. **Özellikleri** altındaki listede, birim testiniz için gereken özellikleri ve test eden kodu seçin. Örneğin, birim testinin ihtiyacı varsa ve test edilmiş kodun internet 'e erişme yeteneğine sahip olması gerekiyorsa **Internet** onay kutusunu seçin.

   > [!NOTE]
   > Seçtiğiniz yetenekler yalnızca birim testinin doğru çalışması için gerekli olan özellikleri içermelidir.

   ![Birim testi bildirimi](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>UWP uygulaması için birim testini kodlayın

Kod Düzenleyicisi 'nde, birim testini düzenleyin ve testiniz için gereken onayları ve mantığı ekleyin.

## <a name="run-unit-tests"></a>Birim testlerini çalıştırma

Çözümü oluşturmak ve test Gezgini 'ni kullanarak birim testini çalıştırmak için:

1. **Test** menüsünde **Windows**' u ve ardından **Test Gezgini**' ni seçin.

2. **Build** menüsünde **Build Solution** öğesini seçin.

   Birim testiniz artık test Gezgini 'nde gösteriliyor.

   > [!NOTE]
   > Test Gezgini 'nde birim testlerinin listesini güncelleştirmek için çözümü derlemeniz gerekir.

3. **Test Gezgini**' nde, oluşturduğunuz birim testini seçin.

4. **Tümünü Çalıştır**' ı seçin.

   ![Birim testi Gezgini &#45; birim testi Çalıştır](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

   > [!TIP]
   > Test Gezgini 'nde listelenen bir veya daha fazla birim testi seçebilir ve sağ tıklayıp **Seçili Testleri Çalıştır**' ı seçebilirsiniz.
   >
   > Ayrıca, **Seçili testlerin hatalarını ayıklamayı**, **testi açmayı** ve **Özellikler** seçeneğini kullanmayı seçebilirsiniz.
   >
   > ![Birim test Gezgini &#45; birim testi bağlam menüsü](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

   Birim testi çalışır. Tamamlandıktan sonra test Gezgini, test durumunu ve geçen süreyi görüntüler ve kaynağa bir bağlantı sağlar.

   ![Birim test Gezgini &#45; testi tamamlandı](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ile UWP uygulamalarını test etme](../test/unit-test-your-code.md)
- [UWP uygulaması oluşturma ve test etme](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)
