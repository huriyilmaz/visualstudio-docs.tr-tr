---
title: UWP uygulamaları için Birim Testleri Oluşturma ve Çalıştırma
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568886"
---
# <a name="walkthrough-create-and-run-unit-tests-for-uwp-apps"></a>İzlenecek yol: UWP uygulamaları için birim testleri oluşturma ve çalıştırma

Visual Studio, Evrensel Windows Platformu (UWP) uygulamalarını birim testi için destek içerir. Visual Studio C#, Visual Basic ve C++ için birim test proje şablonları sağlar.

> [!TIP]
> UWP uygulamaları geliştirme hakkında daha fazla bilgi için [UWP uygulamalarıyla başlarken](/windows/uwp/get-started/)bakın.

Aşağıdaki yordamlar, bir UWP uygulaması için birim testleri oluşturma, çalıştırma ve hata ayıklama adımlarını açıklar.

## <a name="create-a-unit-test-project-for-a-uwp-app"></a>UWP uygulaması için birim test projesi oluşturma

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

2. Yeni proje sayfası **oluştur'un** arama kutusuna **birim testini**girin.

   Şablonlar listesi birim sınama için olanlara filtre filtreler.

3. C# veya Visual Basic için **Birim Test Uygulaması (Evrensel Windows)** şablonunu seçin ve ardından **İleri'yi**seçin.

   ![Visual Studio'da yeni UWP birim test uygulaması oluşturun](media/vs-2019/new-uwp-unit-test-app.png)

4. İsteğe bağlı olarak proje veya çözüm adını ve konumunu değiştirin ve ardından **Oluştur'u**seçin.

5. İsteğe bağlı olarak hedef ve minimum platform sürümlerini değiştirin ve sonra **Tamam'ı**seçin.

Bu adımları tamamladıktan sonra, birim test projesi oluşturulur ve Solution Explorer'da görüntülenir.

![Solution Explorer'da UWP birim test projesi](media/vs-2019/uwp-unit-test-project-solution-explorer.png)

::: moniker-end

::: moniker range="vs-2017"

1. **Dosya** menüsünden **Yeni Proje'yi**seçin.

   **Yeni Proje** iletişim kutusu görüntülenir.

2. Şablonlar altında, birim testleri oluşturmak istediğiniz programlama dilini seçin ve ardından ilişkili Windows Universal birim test kitaplığını seçin. Örneğin, **Visual C#** seçeneğini belirleyin, ardından **Windows Evrensel'i**seçin ve ardından Unit **Test Library'yi (Evrensel Windows)** seçin.

3. (İsteğe bağlı) **Ad** metin kutusuna, proje için kullanmak istediğiniz adı girin.

4. (İsteğe bağlı) **Projeyi** Konum metin kutusuna girerek veya **Gözat** düğmesini seçerek projeyi oluşturmak istediğiniz yolu değiştirin.

5. (İsteğe bağlı) **Çözüm** adı metin kutusuna, çözümünüz için kullanmak istediğiniz adı girin.

6. **Seçili çözüm için Oluştur dizinini** bırakın ve **Tamam** düğmesini seçin.

   ![Özel Birim Test Kütüphanesi](../test/media/unit_test_win8_1.png)

   **Solution Explorer** UWP birim test projesiyle doldurulur ve kod düzenleyicisi UnitTest1 başlıklı varsayılan birim testini görüntüler.

   ![Yeni özel birim test projesi](../test/media/unit_test_win8_unittestexplorer_newprojectcreated.png)

::: moniker-end

## <a name="edit-the-unit-test-projects-uwp-application-manifest-file"></a>Birim test projesinin UWP uygulama bildirim dosyasını düzenlemesi

1. **Solution Explorer'da** *Package.appxmanifest* dosyasına sağ tıklayın ve **Aç'ı**seçin.

2. Manifest **Designer'da** **Yetenekler** sekmesini seçin.

3. **Yetenekler**altındaki listede, birim testinize gereksinim duyduğunuz yetenekleri ve test ettiği kodu seçin. Örneğin, birim testi gerekiyorsa **Internet** onay kutusunu ve test edilen kodun Internet'e erişme özelliğine sahip olması gerekir.

   > [!NOTE]
   > Seçtiğiniz özellikler yalnızca birim testinin düzgün çalışması için gerekli olan yetenekleri içermelidir.

   ![Ünite Test Manifestosu](../test/media/unit_test_win8_.png)

## <a name="code-the-unit-test-for-a-uwp-app"></a>UWP uygulaması için birim testini kodlama

Kod düzenleyicisinde birim testini edin ve testiniz için gereken ileri ve mantığı ekleyin.

## <a name="run-unit-tests"></a>Birim testlerini çalıştırma

Çözümü oluşturmak ve Test Gezgini'ni kullanarak birim testini çalıştırmak için:

1. **Test** menüsünde **Windows'u**seçin ve ardından **Sına Gezgini'ni**seçin.

2. **Yapı** menüsünden **Çözüm Oluştur'u**seçin.

   Birim testiniz artık Test Gezgini'nde gösterilmiştir.

   > [!NOTE]
   > Test Gezgini'ndeki birim testleri listesini güncelleştirmek için çözümü oluşturmanız gerekir.

3. **Test Gezgini'nde**oluşturduğunuz birim testini seçin.

4. **Tümlerini Çalıştır'ı**seçin.

   ![Ünite Test Explorer &#45; çalışma ünitesi testi](../test/media/unit_test_win8_unittestexplorer_contextmenurun.png)

   > [!TIP]
   > Test Gezgini'nde listelenen bir veya daha fazla birim testi seçebilir ve ardından **seçili testleri çalıştır'ı**sağ tıklatıp seçebilirsiniz.
   >
   > Ayrıca, **Seçili Testleri Hata Ayıklama**, **Test Aç**ve **Özellikler** seçeneğini belirleyebilirsiniz.
   >
   > ![Ünite Test Explorer &#45; ünite test bağlam menüsü](../test/media/unit_test_win8_unittestexplorer_contextmenu.png)

   Birim testi çalışır. Tamamlandıktan sonra, Test Gezgini test durumunu ve geçen süreyi görüntüler ve kaynağa bir bağlantı sağlar.

   ![Ünite Test Explorer &#45; testi tamamlandı](../test/media/unit_test_win8_unittestexplorer_done.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ile UWP uygulamalarını test edin](../test/unit-test-your-code.md)
- [Bir UWP uygulaması oluşturma ve test edin](/azure/devops/pipelines/apps/windows/universal?tabs=vsts)
