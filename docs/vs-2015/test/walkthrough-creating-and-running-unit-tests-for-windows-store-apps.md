---
title: 'İzlenecek yol: Windows Mağazası uygulamaları için birim testleri oluşturma ve çalıştırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests
- unit tests, Windows Store apps
- unit tests, running
ms.assetid: dd3e8a6a-b366-433e-a409-b9a9b89da89a
caps.latest.revision: 23
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f5e62fe83d644b577d7d0a5f87312642f438c490
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851178"
---
# <a name="walkthrough-creating-and-running-unit-tests-for-windows-store-apps"></a>İzlenecek yol: Windows Mağazası Uygulamaları için Birim Testleri Oluşturma ve Çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio, birim testi yönetilen [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamaları için destek içerir ve Visual C#, Visual Basic ve Visual C++için birim test kitaplığı şablonları içerir.

> [!TIP]
> [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [Windows Mağazası uygulamalarını](https://msdn.microsoft.com/windows/apps/br211386.aspx)kullanmaya başlama.

 Visual Studio aşağıdaki birim testi işlevini sağlar:

- [Birim testi projeleri oluşturma](#CreateAndRunUnitTestWin8Tailored_Create)

- [Birim testi projesinin bildirimini düzenleme](#CreateAndRunUnitTestWin8Tailored_Manifest)

- [Birim testini kodlayın](#CreateAndRunUnitTestWin8Tailored_Code)

- [Birim testlerini çalıştırma](#CreateAndRunUnitTestWin8Tailored_Run)

  Aşağıdaki yordamlarda, yönetilen Windows 8 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulaması için birim testleri oluşturma, çalıştırma ve hata ayıklama adımları açıklanır.

## <a name="prerequisites"></a>Prerequisites
 {1&gt;Visual Studio&lt;1}

## <a name="CreateAndRunUnitTestWin8Tailored_Create"></a>Birim testi projeleri oluşturma

#### <a name="to-create-a-unit-test-project-for-a-windows-store-app"></a>Bir Windows Mağazası uygulaması için birim testi projesi oluşturmak için

1. Gelen **dosya** menüsünde seçin **yeni proje**.

     Yeni proje iletişim kutusu görüntülenir.

2. Şablonlar ' ın altında, birim testi oluşturmak istediğiniz programlama dilini seçin ve ardından ilişkili [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] birim testi kitaplığı ' nı seçin. Örneğin, **görsel C#**  ' i seçin, ardından **Windows Mağazası**' nı seçin ve ardından **birim testi kitaplığı (Windows Mağazası uygulamaları)** öğesini seçin.

    > [!NOTE]
    > Visual Studio, Visual C#, Visual Basic ve görsel C++için birim testi kitaplığı şablonları içerir.

3. Seçim **Ad** metin kutusuna [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]birim testi projesi için kullanmak istediğiniz adı girin.

4. Seçim Projeyi **konum** metin kutusuna girerek oluşturmak istediğiniz yolu değiştirin veya **Araştır** düğmesini seçin.

5. (İsteğe bağlı) İçinde **çözüm** ad metin kutusunda, çözümünüz için kullanmak istediğiniz ismi girin.

6. Bırakın **çözüm için dizin oluştur** seçeneği seçili ve seçin **Tamam** düğmesi.

     ![Özel birim testi kitaplığı](../test/media/unit-test-win8-1.png "Unit_Test_Win8_1")

     Çözüm Gezgini yeni [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]birim testi projem ile doldurulmuştur ve kod Düzenleyicisi, UnitTest1 başlıklı varsayılan birim testini görüntüler.

     ![Yeni özel birim testi projesi](../test/media/unit-test-win8-unittestexplorer-newprojectcreated.png "Unit_Test_Win8_UnitTestExplorer_NewProjectCreated")

## <a name="CreateAndRunUnitTestWin8Tailored_Manifest"></a>Birim testi projesinin bildirimini düzenleme
 Uygulamayı çalıştırmak için gerekli özellikleri sağlamak üzere birim test projesi bildiriminin düzenlenmesi gerekebilir.

#### <a name="to-edit-the-unit-test-projects-windows-store-application-manifest-file"></a>Birim testi projesinin Windows Mağazası uygulaması bildirim dosyasını düzenlemek için

1. Çözüm Gezgini yeni [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] birim testi projesinde Package. appxmanifest dosyasına sağ tıklayın ve **Aç**' ı seçin.

     Bildirim Tasarımcısı düzenlenmek üzere görüntülenir.

2. Bildirim tasarımcısında **yetenekler** sekmesini seçin.

3. Listenin altında **özellikleri**, birim sınamanız ve kod gereken yetenekleri seçin sahip sınamanız. Örneğin, **Internet** birim testi ve test ettiği kodun onay kutusu İnternet'e erişme özelliği olması gerekir.

    > [!NOTE]
    > Seçtiğiniz yetenekler yalnızca [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] birim testinin düzgün çalışması için gerekli olan özellikleri içermelidir. Bu özelliklerde, test edilen [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] uygulamasının bir parçası olmayan ve genellikle test altındaki [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]uygulaması için belirtilen yeteneklerin bir alt kümesi olması gereken özellikleri içermesi gerekmez.

     Bildirim Tasarımcısı hakkında daha fazla bilgi için bkz. [bildirim tasarımcısını kullanarak Windows 8.1 uygulama paketi yapılandırma](https://msdn.microsoft.com/library/24c58b7f-9c6d-41c3-b385-c1e8497d5b2d).

     ![Birim testi bildirimi](../test/media/unit-test-win8.png "Unit_Test_Win8_")

## <a name="CreateAndRunUnitTestWin8Tailored_Code"></a>Birim testini kodlayın

#### <a name="to-code-the-unit-test-for-a-windows-store-app"></a>Windows Mağazası uygulaması için birim testini kodlayın

1. Kod Düzenleyicisi 'nde, birim testini düzenleyin ve testiniz için gereken onayları ve mantığı ekleyin.

     Daha fazla bilgi için MSDN Kitaplığı 'ndaki [onaylama sınıflarını kullanma](https://msdn.microsoft.com/library/ms182530.aspx) bölümüne bakın.

## <a name="CreateAndRunUnitTestWin8Tailored_Run"></a>Birim testlerini çalıştırma

#### <a name="to-build-the-solution-and-run-the-unit-test-using-test-explorer"></a>Çözümü derleyin ve Test Gezgini'ni kullanarak birim testini çalıştırmak için

1. Üzerinde **Test** menüsünde seçin **Windows**ve ardından **Test Gezgini**.

     Test Gezgini, testiniz listelenmeden görüntülenir.

2. Gelen **derleme** menüsünde seçin **Çözümü Derle**.

     Birim testiniz artık listelenir.

    > [!NOTE]
    > Test Gezgini'nde birim testleri listesini güncelleme çözümünü oluşturmanız gerekir.

    > [!WARNING]
    > Visual Studio bilinen sorun: test projesini oluşturmadan önce test Gezgini 'ni açmanız gerekir.

3. Test Gezgini ' nde, oluşturduğunuz birim testini seçin.

    > [!TIP]
    > Test Gezgini kaynak koda bir bağlantı yanındaki sağlar **kaynak:** .

4. Seçin **çalıştırması**.

     ![Birim testi Gezgini &#45; çalışma birimi testi](../test/media/unit-test-win8-unittestexplorer-contextmenurun.png "Unit_Test_Win8_UnitTestExplorer_ContextMenuRun")

    > [!TIP]
    > Explorer'da listelenen bir veya daha fazla birim testleri seçebilir ve ardından sağ tıklatın ve seçin **seçili Testleri Çalıştır**.
    >
    >  Ayrıca, seçebileceğiniz **seçilen Testlerde Hata Ayıkla**, **açık Test**ve **özellikleri** seçeneği.
    >
    >  ![Birim test Gezgini &#45; UNI test bağlam menüsü](../test/media/unit-test-win8-unittestexplorer-contextmenu.png "Unit_Test_Win8_UnitTestExplorer_ContextMenu")

     Birim testi çalışır. Tamamlandıktan sonra test Gezgini, test durumunu, geçen süreyi görüntüler ve kaynağa bir bağlantı sağlar.

     ![Birim test Gezgini &#45; testi tamamlandı](../test/media/unit-test-win8-unittestexplorer-done.png "Unit_Test_Win8_UnitTestExplorer_Done")

## <a name="external-resources"></a>Dış Kaynaklar

### <a name="videos"></a>Videolar
 [Channel 9: XAML kullanılarak oluşturulan Windows Mağazası uygulamalarınızı birim testi yapma](https://channel9.msdn.com/Events/BUILD/BUILD2011/TOOL-529T)

### <a name="forums"></a>Forumlar
 [Visual Studio birim testi](https://social.msdn.microsoft.com/Forums/en/vsunittest/threads)

### <a name="msdn-library"></a>MSDN Kitaplığı
 [MSDN Kitaplığı – mevcut kod için birim testleri oluşturma ve çalıştırma (Visual Studio 2010)](https://msdn.microsoft.com/library/hh270865(v=vs.110).aspx)

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio Ile mağaza uygulamalarını test etme](../test/testing-store-apps-with-visual-studio.md) [ve Team Foundation Build kullanarak Windows Mağazası uygulaması oluşturma ve test](https://msdn.microsoft.com/library/d0ca17bb-deae-4f3d-a18d-1a99bebceaa9) etme
