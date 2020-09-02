---
title: C++ Kullanmaya Başlarken
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 99c73344-86ba-4b08-9e15-f6111cc04185
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 001b394d86e56b172bb1a50c335bd8ba5bcacb15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645625"
---
# <a name="getting-started-with-c-in-visual-studio"></a>Visual Studio'da C++ Kullanmaya Başlarken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu yönergeyi tamamlayarak, Visual Studio ile uygulama geliştirirken kullanabileceğiniz birçok araç ve iletişim kutusu hakkında bilgi sahibi olacaksınız. Tümleşik geliştirme ortamında (IDE) çalışma hakkında daha fazla bilgi edinirken basit bir "Merhaba, Dünya" stili uygulama oluşturacaksınız.

 Bu konu aşağıdaki bölümleri içermektedir:

 [Visual Studio 'Da oturum açın](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_Configure)

 [Basit bir uygulama oluşturma](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_CreateApp)

 [Uygulamaya kod ekleme](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_AddCode)

 [Uygulamanın hatalarını ayıklama ve test etme](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_DebugTest)

 [Uygulamanın yayın sürümünü oluştur](../ide/getting-started-with-cpp-in-visual-studio.md#BKMK_BuildRelease)

## <a name="sign-in-to-visual-studio"></a><a name="BKMK_Configure"></a> Visual Studio 'Da oturum açın
 Visual Studio 'Yu ilk kez başlattığınızda, Live veya Outlook gibi bir Microsoft hesabı kullanarak oturum açma şansı vermiş olursunuz. Oturum açmak, ayarlarınızın tüm cihazlarınızda eşitlenmesini sağlar. Daha fazla bilgi için bkz. [Visual Studio 'Da oturum açma](../ide/signing-in-to-visual-studio.md)

 Şekil 1: Visual Studio IDE

 ![Visual C&#43;&#43; ayarları uygulanmış IDE](../ide/media/c-ide-defaultenvironmentlayout.png "C++ IDE_DefaultEnvironmentLayout")

 Visual Studio 'Yu açtıktan sonra IDE 'nin üç temel parçasını görebilirsiniz: araç pencereleri, menüler ve araç çubukları ve ana pencere alanı. Araç pencereleri, **Hızlı Başlat**, menü çubuğu ve en üstteki Standart araç çubuğu ile uygulama penceresinin sol ve sağ taraflarına yerleştirilir. Uygulama penceresinin Merkezi **Başlangıç sayfasını**içerir. Bir çözüm veya proje açtığınızda, düzenleyiciler ve tasarımcılar bu alanda görüntülenir. Uygulama geliştirirken zamanınızın çoğunu bu orta alanda geçireceksiniz.

## <a name="create-a-simple-application"></a><a name="BKMK_CreateApp"></a> Basit bir uygulama oluşturma
 Visual Studio 'da bir uygulama oluşturduğunuzda, önce bir proje ve bir çözüm oluşturursunuz. Bu örnekte, bir Windows konsol uygulaması oluşturacaksınız.

#### <a name="to-create-a-console-app"></a>Konsol uygulaması oluşturmak için

1. Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.

    ![Menü çubuğunda dosya, yeni, proje ' yi seçin.](../ide/media/exploreide-filenewproject.png "ExploreIDE-FileNewProject")

2. **Visual C++** kategorisinde **Win32 konsol uygulaması** şablonunu seçin ve ardından projeyi adlandırın `GreetingsConsoleApp` .

    ![Win32 konsol uygulaması şablonu](../ide/media/c-ide-newprojectdlg.png "C++ IDE_NewProjectDlg")

3. Win32 uygulama Sihirbazı göründüğünde **son** düğmesini seçin.

    ![Win32 konsol uygulaması Sihirbazı](../ide/media/c-ide-win32consoleappwizard.png "C++ IDE_Win32ConsoleAppWizard")

   Bir Win32 konsol uygulaması için temel dosyalarla birlikte bulunan ve **Çözüm Gezgini**' ye otomatik olarak yüklenen, Alaingsconsoleapp projesi ve çözümü oluşturulur. , Kod Düzenleyicisi 'nde,,,,,. cpp dosyası açılır. Aşağıdaki öğeler **Çözüm Gezgini**görüntülenir:

   Şekil 4: proje öğeleri

   ![Çözüm Gezgini çözüm dosyaları](../ide/media/c-ide-solutioncontents.png "C++ IDE_SolutionContents")

## <a name="add-code-to-the-application"></a><a name="BKMK_AddCode"></a> Uygulamaya kod ekleme
 Daha sonra, konsol penceresinde "Hello" sözcüğünü göstermek için kod ekleyeceksiniz.

#### <a name="to-display-hello-in-the-console-window"></a>Konsol penceresinde "Merhaba" göstermek için

1. Inıngingsconsoleapp. cpp dosyasında, satırdan önce boş bir satır girin `return 0;` ve ardından aşağıdaki kodu girin:

    ```
    cout << "Hello\n";
    ```

     Altında kırmızı dalgalı çizgi görünür `cout` . Üzerine geldiğinizde bir hata iletisi görüntülenir.

     ![Cout için hata metni](../ide/media/c-ide-couterror.png "C++ IDE_CoutError")

     Hata iletisi **hata listesi** penceresinde de görüntülenir. Pencereyi, menü çubuğunda **Görünüm**, **hata listesi**seçeneğini belirleyerek görüntüleyebilirsiniz.

     [cout](https://msdn.microsoft.com/library/d87db6c3-e4e1-4d09-9ec5-458f55018257) , \<iostream\> üstbilgi dosyasına dahildir.

2. İostream üst bilgisini eklemek için, sonrasında aşağıdaki kodu girin `#include "stdafx.h"` :

    ```
    #include \<iostream\>
    using namespace std;
    ```

     Büyük olasılıkla, girdiğiniz karakterler için öneriler sağlayan bir kutunun kod girdiğinizde göründü olduğunu fark etmiş olabilirsiniz. Bu kutu, sınıf veya arabirim üyelerini ve parametre bilgilerini listeleme dahil olmak üzere kodlama istemleri sağlayan C++ IntelliSense 'in bir parçasıdır. Önceden tanımlanmış kod blokları olan kod parçacıklarını da kullanabilirsiniz. Daha fazla bilgi için bkz. IntelliSense ve [kod parçacıkları](../ide/code-snippets.md) [kullanma](../ide/using-intellisense.md) .

     Hatayı düzelttikten sonra kırmızı dalgalı çizgi `cout` kaybolur.

3. Dosyadaki değişiklikleri kaydedin.

     ![Cout hatasını düzelten kod](../ide/media/c-ide-coutfix.png "C++ IDE_CoutFix")

## <a name="debug-and-test-the-application"></a><a name="BKMK_DebugTest"></a> Uygulamanın hatalarını ayıklama ve test etme
 "Hello" sözcüğünün konsol penceresinde görünüp görüntülenmediğini görmek için, "Merhaba" hata ayıklaması yapabilirsiniz.

#### <a name="to-debug-the-application"></a>Uygulamada hata ayıklamak için

- Hata ayıklayıcıyı başlatın.

     ![Hata ayıklama menüsünde hata ayıklamayı Başlat komutu](../ide/media/exploreide-startdebugging.png "ExploreIDE-StartDebugging")

     Hata ayıklayıcı başlatılır ve kodu çalıştırır. Konsol penceresi (bir komut istemi gibi görünen ayrı bir pencere) birkaç saniye boyunca görünür, ancak hata ayıklayıcı çalışmayı durdurduktan sonra hızlı bir şekilde kapanır. Metni görmek için, program yürütmeyi durdurmak için bir kesme noktası ayarlamanız gerekir.

#### <a name="to-add-a-breakpoint"></a>Kesme noktası eklemek için

1. Satırdaki menü çubuğundan bir kesme noktası ekleyin `return 0;` . Ayrıca, bir kesme noktası ayarlamak için sol kenar boşluğunu de tıklayabilirsiniz.

    ![Hata ayıklama menüsünde kesme noktasını Aç komutu](../ide/media/exploreide-togglebreakpoint.png "ExploreIDE-ToggleBreakpoint")

    Düzenleyici penceresinin en sol kenar boşluğunda, kod satırının yanında kırmızı bir daire görünür.

2. Hata ayıklamayı başlatmak için F5 tuşunu seçin.

    Hata ayıklayıcı başlar ve **Hello**sözcüğünün gösterildiği bir konsol penceresi görüntülenir.

    ![Windows komut Istemi penceresinde Merhaba metin](../ide/media/c-ide-hellocommandwindow.png "C++ IDE_HelloCommandWindow")

3. Hata ayıklamayı durdurmak için SHIFT + F5 tuşlarına basın.

   Daha fazla bilgi için bkz. [Konsol projeleri](../debugger/debugging-preparation-console-projects.md).

## <a name="build-a-release-version-of-the-app"></a><a name="BKMK_BuildRelease"></a> Uygulamanın yayın sürümünü oluştur
 Her şeyin çalıştığını doğruladığınıza göre artık, uygulamanın bir yayın derlemesini hazırlayabilirsiniz.

#### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Çözüm dosyalarını temizlemek ve yayın sürümünü oluşturmak için

1. Menü çubuğundan, önceki derlemeler sırasında oluşturulan ara dosyaları ve çıktı dosyalarını silin.

    ![Derleme menüsündeki Çözümü Temizle komutu](../ide/media/exploreide-cleansolution.png "ExploreIDE-CleanSolution")

2. Insdingsconsoleapp için derleme yapılandırmasını **hata ayıklamadan** **Release**olarak değiştirin.

    ![Uygulamanın yayın sürümünü oluşturma](../ide/media/c-ide-changingbuildtorelease.png "C++ IDE_ChangingBuildtoRelease")

3. Çözümü derleyin.

    ![Build menüsünde çözüm komutu oluştur](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

   Tebrikler, bu izlenecek yolu tamamladınız! Daha fazla örnek araştırmak isterseniz bkz. [Visual Studio örnekleri](../ide/visual-studio-samples.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Izlenecek yol: basit bir uygulama](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md) [üretkenlik Ipuçları](../ide/productivity-tips-for-visual-studio.md) oluşturma Visual [Studio örnekleri](../ide/visual-studio-samples.md) [Visual Studio ile geliştirmeye başlama](../ide/get-started-developing-with-visual-studio.md)
