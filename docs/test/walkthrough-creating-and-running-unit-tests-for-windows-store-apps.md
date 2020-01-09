---
title: Oluşturma ve UWP uygulamaları için birim testleri çalıştırma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, UWP apps
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 4109f743caf7c62450591f78e90b92113fc4107e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568886"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>İzlenecek yol: UWP uygulamaları için birim testleri oluşturma ve çalıştırma

Visual Studio birim testi Evrensel Windows Platformu (UWP) uygulamaları için destek içerir. Visual Studio, Visual Basic ve C# C++için birim testi proje şablonları sağlar.

> [!TIP]
> UWP uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [UWP uygulamaları kullanmaya başlama](/windows/uwp/get-started/).

Aşağıdaki yordamlarda, UWP uygulaması için birim testleri oluşturma, çalıştırma ve hata ayıklama adımları açıklanır.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>Bir UWP uygulaması için birim test projesi oluşturma

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

2. **Yeni proje oluştur** sayfasının arama kutusunda **birim testi**girin.

   Şablon listesi, birim testi için olanlarla filtreler.

3. Ya da C# Visual Basic Için **birim testi uygulaması (Evrensel Windows)** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Visual Studio 'da yeni UWP birim testi uygulaması oluşturma](media/vs-2019/new-uwp-unit-test-app.png)

4. İsteğe bağlı olarak proje veya çözüm adını ve konumunu değiştirip **Oluştur**' u seçin.

5. İsteğe bağlı olarak hedef ve en düşük platform sürümlerini değiştirip **Tamam**' ı seçin.

Bu adımları tamamladıktan sonra, birim test projesi oluşturulur ve Çözüm Gezgini içinde görüntülenir.

![Çözüm Gezgini UWP birim testi projesi](media/vs-2019/uwp-unit-test-project-solution-explorer.png)

::: moniker-end

::: moniker range="vs-2017"

1. Gelen **dosya** menüsünde seçin **yeni proje**.

   **Yeni proje** iletişim kutusunu görüntüler.

2. Şablonlar'ın altında birim testleri oluşturun ve sonra kitaplık ilişkili Windows Evrensel birim testi için kullanmak istediğiniz programlama dilini seçin. Örneğin, **Visual C#** , ardından **Windows Evrensel**ve ardından **birim testi kitaplığı (Evrensel Windows)** .

3. (İsteğe bağlı) İçinde **adı** metin kutusuna proje için kullanmak istediğiniz adı girin.

4. (İsteğe bağlı) Girerek projeyi oluşturmak istediğiniz yolu değiştirmek **konumu** metin veya seçerek **Gözat** düğmesi.

5. (İsteğe bağlı) İçinde **çözüm** ad metin kutusunda, çözümünüz için kullanmak istediğiniz ismi girin.

6. Bırakın **çözüm için dizin oluştur** seçeneği seçili ve seçin **Tamam** düğmesi.

   ![Özel olarak uyarlanmış bir birim testi kitaplığı](../test/media/unit_test_win8_1.png)

   **Çözüm Gezgini** doldurulur UWP birim testi projesi ve Kod Düzenleyicisi, UnitTest1 başlıklı varsayılan birim sınamasını görüntüler.

   ![Yeni özel olarak uyarlanmış bir birim test projesi](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

::: moniker-end

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Birim test projesinin UWP uygulama bildirim dosyasını Düzenle

1. İçinde **Çözüm Gezgini**, sağ *Package.appxmanifest* seçin ve dosya **açık**.

2. İçinde **bildirim Tasarımcısı**, seçin **özellikleri** sekmesi.

3. Listenin altında **özellikleri**, birim sınamanız ve kod gereken yetenekleri seçin sahip sınamanız. Örneğin, **Internet** birim testi ve test ettiği kodun onay kutusu İnternet'e erişme özelliği olması gerekir.

   > [!NOTE]
   > Seçtiğiniz yetenekler yalnızca birim testi düzgün çalışması gerekli olan yetenekleri içermelidir.

   ![Birim Test bildirimi](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>Bir UWP uygulaması için birim testini kodlama

Kod Düzenleyicisi 'nde, birim testini düzenleyin ve testiniz için gereken onayları ve mantığı ekleyin.

## <a name="run-unit-tests"></a>Birim testlerini çalıştırma

Çözümü oluşturmak ve test Gezgini 'ni kullanarak birim testini çalıştırmak için:

1. Üzerinde **Test** menüsünde seçin **Windows**ve ardından **Test Gezgini**.

2. Gelen **derleme** menüsünde seçin **Çözümü Derle**.

   Birim testiniz artık test Gezgini 'nde gösteriliyor.

   > [!NOTE]
   > Test Gezgini'nde birim testleri listesini güncelleme çözümünü oluşturmanız gerekir.

3. İçinde **Test Gezgini**, oluşturduğunuz birim sınamayı seçin.

4. Seçin **çalıştırması**.

   ![Birim Test Gezgini &#45; birim testi çalıştırma](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

   > [!TIP]
   > Test Gezgini 'nde listelenen bir veya daha fazla birim testi seçebilir ve sağ tıklayıp **Seçili Testleri Çalıştır**' ı seçebilirsiniz.
   >
   > Ayrıca, seçebileceğiniz **seçilen Testlerde Hata Ayıkla**, **açık Test**ve **özellikleri** seçeneği.
   >
   > ![Birim testi Gezgini &#45; birim testi bağlam menüsü](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

   Birim testi çalışır. Tamamlandıktan sonra test Gezgini, test durumunu ve geçen süreyi görüntüler ve kaynağa bir bağlantı sağlar.

   ![Birim Test Gezgini &#45; test tamamlandı](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ile UWP uygulamalarını test etme](../test/unit-test-your-code.md)
- [Yapı ve test bir UWP uygulaması](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)
