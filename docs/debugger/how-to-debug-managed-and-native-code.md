---
title: 'Öğretici: C# ve C++ kodunda hata ayıklama (karma mod)'
description: Karma mod hata ayıklama kullanarak bir .NET Core veya .NET Framework dll'de hata ayıklamayı öğrenin
ms.custom: seodec18
ms.date: 11/02/2018
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- mixed mode debugging
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 3cc80af05e180992d5905a8b6202d7c7a219365bbfae1ab4e62ee22a02db3f39
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121362210"
---
# <a name="tutorial-debug-c-and-c-in-the-same-debugging-session"></a>Öğretici: Aynı hata ayıklama oturumunda C# ve C++ hata ayıklaması

Visual Studio, karma mod hata ayıklama olarak adlandırılan bir hata ayıklama oturumunda birden fazla hata ayıklayıcı türünü etkinleştirmenizi sağlar. Bu öğreticide, tek bir hata ayıklama oturumunda hem yönetilen hem de yerel kodda hata ayıklamayı öğrenirsiniz.

Bu öğretici, yönetilen bir uygulamanın yerel kodunda hata ayıklamayı gösterir, ancak yerel bir uygulamanın [yönetilen kodunda da hata ayıkabilirsiniz.](../debugger/how-to-debug-in-mixed-mode.md) Hata ayıklayıcısı ayrıca [Python'da](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md)ve yerel kodda hata ayıklama ve betik hata ayıklayıcısını uygulama türleri gibi uygulama türlerinde kullanma gibi diğer karma mod hata ayıklama ASP.NET.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Basit bir yerel DLL oluşturma
> * DLL'i çağıran basit .NET Framework bir .NET Core veya uygulama oluşturma
> * Karma mod hata ayıklamayı yapılandırma
> * Hata ayıklayıcıyı başlatma
> * Yönetilen uygulamada kesme noktası isabeti
> * Yerel koda adımla

## <a name="prerequisites"></a>Önkoşullar

Aşağıdaki iş Visual Studio yüklü olması gerekir:
- **C++ ile masaüstü geliştirme**
- Oluşturmak **istediğiniz uygulama türüne** **bağlı olarak .NET masaüstü** geliştirme veya .NET Core platformlar arası geliştirme.

Uygulamanız yoksa, Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/downloads/) indirmeler sayfasına gidin.

Yüklü Visual Studio ancak ihtiyacınız olan iş yükleri yoksa, yeni Project  iletişim kutusunun sol bölmesindeki Visual Studio Visual Studio Yükleyicisi **Aç'ı** seçin. Aşağıdaki Visual Studio Yükleyicisi iş yüklerini seçin ve ardından Değiştir'i **seçin.**

## <a name="create-a-simple-native-dll"></a>Basit bir yerel DLL oluşturma

**DLL projesinin dosyalarını oluşturmak için:**

1. Visual Studio açın ve proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama **kutusunu açmak için Ctrl + Q** tuşlarına basın, Boş **Project** yazın, Şablonlar'ı **seçin** ve ardından C++ için **boş Project'ı** seçin. Görüntülenen iletişim kutusunda Oluştur'a **tıklayın.** Ardından, Mixed_Mode_Debugging **gibi bir ad yazın ve** Oluştur'a **tıklayın.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **Dosya'Project.**  >    >   Yeni proje iletişim **kutusunun sol** bölmesinde, Visual C++ **altında** Diğer'i seçin ve ardından orta bölmede Boş  **proje'yi Project.** Ardından, Mixed_Mode_Debugging **gibi bir ad yazın** ve Tamam'a **tıklayın.**
    ::: moniker-end

    Boş Proje Şablonu'Project  görmüyorsanız Araçlar Araçları ve Özellikleri Al... 'a gidin  >  **ve** Visual Studio Yükleyicisi. Uygulama Visual Studio Yükleyicisi başlatıyor. **C++ ile masaüstü geliştirme iş yükünü ve** ardından Değiştir'i **seçin.**

    Visual Studio projeyi oluşturur.

1. Bu **Çözüm Gezgini** Kaynak **Dosyalar'ı seçin ve** ardından Yeni Öğe   >  **Project'ı seçin.** Veya Kaynak Dosyalar'a **sağ tıklar ve Yeni** Öğe **Ekle'yi**  >  **seçin.**

1. Yeni Öğe **iletişim kutusunda** C++ dosyası **(.cpp) öğesini seçin.** Ad **alanına Mixed_Mode.cpp** **yazın** ve Ekle'yi **seçin.**

    Visual Studio yeni C++ dosyasını dosyasına **Çözüm Gezgini.**

1. Aşağıdaki kodu *Mixed_Mode.cpp içine kopyalayın:*

    ```cpp
    #include "Mixed_Mode.h"
    ```

1. Yeni **Çözüm Gezgini** Üst Bilgi **Dosyaları'Project**   >  **seçin.** Veya Üst Bilgi Dosyaları'a **sağ tıklar ve** Yeni Öğe **Ekle'yi**  >  **seçin.**

1. Yeni Öğe **iletişim kutusunda** Üst bilgi dosyası **(.h) öğesini seçin.** Ad **alanına Mixed_Mode.h** **yazın** ve Ekle'yi **seçin.**

   Visual Studio yeni üst bilgi dosyasını dosyasına **Çözüm Gezgini.**

1. Aşağıdaki kodu *Mixed_Mode.h içine kopyalayın:*

    ```cpp
    #ifndef MIXED_MODE_MULTIPLY_HPP
    #define MIXED_MODE_MULTIPLY_HPP

    extern "C"
    {
      __declspec(dllexport) int __stdcall mixed_mode_multiply(int a, int b) {
        return a * b;
      }
    }
    #endif
    ```

1. Dosyaları **kaydetmek için** Dosya  >  **Tamamını** Kaydet'i seçin veya **Ctrl** + **Shift** + **S** tuşlarına basın.

**DLL projesini yapılandırmak ve derlemek için:**

1. Uygulama araç Visual Studio hata ayıkla **ve** **x86 veya** **x64 platform'u** seçin. Çağıran uygulamanız her zaman 64 bit modunda çalışan .NET Core olacaksa platform olarak **x64'ü** seçin.

1. Bu **Çözüm Gezgini** proje **düğümünü Mixed_Mode_Debugging** Özellikler simgesini seçin  veya proje düğümüne sağ tıklar ve Özellikler'i **seçin.**

1. Özellikler bölmesinin  üst kısmında Yapılandırma'nın Etkin **(Hata Ayıklama)** olarak ve **Platform'un** da araç çubuğunda ayarla aynı olduğundan emin olun: **x64** veya x86 platformu **için Win32.** 

   > [!IMPORTANT]
   > Platformu **x86'dan** **x64'e** veya tam tersi bir şekilde değiştirecek olursanız, yeni platformun özelliklerini yeniden yapılandırmanız gerekir.

1. Sol **bölmede Yapılandırma** Özellikleri'nin altında, **Bağlantı Noktası** Gelişmiş'i seçin ve Giriş Noktası Yok seçeneğinin  >  yanındaki açılan **listeden** Hayır'ı **seçin.** Hayır olarak değiştirmek **zorundaysanız Uygula'ya** **seçin.**

1. Yapılandırma **Özellikleri'nin** altında **Genel'i** seçin ve Yapılandırma Türü'nin yanındaki açılan **listeden** Dinamik Kitaplık **(.dll) öğesini seçin.** **Uygula**’yı ve sonra **Tamam**’ı seçin.

   ![Yerel DLL'ye geçiş](../debugger/media/mixed-mode-set-as-native-dll.png)

1. projesinde projeyi seçin **Çözüm Gezgini** Çözümü Derleme'yi seçin, F7 tuşuna basın veya projeye sağ  >  tıklar ve Derleme'yi **seçin.** 

   Projenin hatasız oluşturması gerekir.

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>DLL'i çağıran basit bir yönetilen uygulama oluşturma

1. Yeni Visual Studio ve yeni bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. **Arama kutusunu açmak için Ctrl + Q** yazın, konsol **yazın,** Şablonlar'ı seçin ve ardından C# için .NET Core için Konsol Uygulaması veya Konsol Uygulaması **(.NET Framework)** seçin.  Görüntülenen iletişim kutusunda, Sonraki'yi **seçin.**

    Ardından, Mixed_Mode_Calling_App **gibi bir** ad yazın ve Ardından **veya** **Oluştur**'a tıklayın. (Varsa bu seçenek hangisidir?).

    .NET Core için önerilen hedef çerçeveyi (.NET Core 3.1) veya .NET 5'i seçin ve ardından Oluştur'a **seçin.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **Dosya'Project.**  >    >   Yeni proje iletişim  kutusunun sol bölmesinde, **Visual C#** altında **Windows Desktop'ı** seçin ve orta bölmede Konsol Uygulaması **(.NET Framework)** veya Konsol Uygulaması **(.NET Core)** seçeneğini seçin.

    Ardından, Mixed_Mode_Calling_App **gibi bir ad yazın** ve Tamam'a **tıklayın.**
    ::: moniker-end

    Doğru proje şablonunu görmüyorsanız Araçlar Araçları ve Özellikleri Al... 'a gidin  >  **ve** Visual Studio Yükleyicisi. Hedef **çerçevenize bağlı olarak .NET Core platformlar** arası geliştirme veya **.NET masaüstü** geliştirme iş yükünü seçin ve ardından Değiştir'i **seçin.**

    > [!NOTE]
    > Ayrıca yeni yönetilen projeyi mevcut C++ çözümünüze de eklemek mümkündür. Karma mod hata ayıklama görevini daha zor hale etmek için projeyi yeni bir çözümde oluşturuyoruz.

   Visual Studio boş projeyi oluşturur ve projesinde **Çözüm Gezgini.**

1. *Program.cs'de yer alan tüm kodu* aşağıdaki kodla değiştirin:

    ```csharp
    using System;
    using System.Runtime.InteropServices;

    namespace Mixed_Mode_Calling_App
    {
        public class Program
        {
            // Replace the file path shown here with the
            // file path on your computer. For .NET Core, the typical (default) path
            // for a 64-bit DLL might look like this:
            // C:\Users\username\source\repos\Mixed_Mode_Debugging\x64\Debug\Mixed_Mode_Debugging.dll
            // Here, we show a typical path for a DLL targeting the **x86** option.
            [DllImport(@"C:\Users\username\source\repos\Mixed_Mode_Debugging\Debug\Mixed_Mode_Debugging.dll", EntryPoint =
            "mixed_mode_multiply", CallingConvention = CallingConvention.StdCall)]
            public static extern int Multiply(int x, int y);
            public static void Main(string[] args)
            {
                int result = Multiply(7, 7);
                Console.WriteLine("The answer is {0}", result);
                Console.ReadKey();
            }
        }
    }
    ```

1. Yeni kodda, dosyasındaki dosya yolunu, yeni oluşturduğunuz dosya `[DllImport]` *Mixed_Mode_Debugging.dll* yoluyla değiştirin. İpuçları için kod açıklamasına bakın. Kullanıcı adı yer tutucusunu değiştir *mutlaka* değiştirin.

1. Dosyayı **kaydetmek için** Dosya Kaydet  >  **Program.cs'yi** seçin veya **Ctrl** + **S** tuşlarına basın.

## <a name="configure-mixed-mode-debugging"></a>Karma mod hata ayıklamayı yapılandırma

1. Bu **Çözüm Gezgini** proje **düğümünü Mixed_Mode_Calling_App** Özellikler simgesini seçin  veya proje düğümüne sağ tıklar ve Özellikler'i **seçin.**

1. Sol **bölmede** Hata Ayıkla'ya tıklayın, Yerel kodda hata ayıklamayı etkinleştir onay kutusunu seçin ve ardından değişiklikleri kaydetmek için özellikler sayfasını kapatın. 

    ![Karma mod hata ayıklamayı etkinleştirme](../debugger/media/mixed-mode-enable-native-code-debugging.png)

## <a name="set-a-breakpoint-and-start-debugging"></a>Kesme noktası ayarlama ve hata ayıklamayı başlatma

1. C# projesinde *Program.cs'yi açın.* En sol kenar boşluğuna tıklayarak, satırı seçerek ve **F9** tuşuna basarak veya satıra sağ tıklar ve Kesme Noktası Ekle Kesme Noktası seçeneğini kullanarak aşağıdaki kod satırına bir  >  **kesme noktası ayarlayın.**

    ```csharp
    int result = Multiply(7, 7);
    ```

    Kesme noktası ayar olarak sol kenar boşluğunda kırmızı bir daire görünür.

1. **F5 tuşuna** basın, araç çubuğundaki yeşil Visual Studio seçin veya Hata Ayıklamayı Başlat'ı  >   seçerek hata ayıklamayı başlatın.

   Hata ayıklayıcısı, ayar istediğiniz kesme noktası üzerinde duraklatılır. Sarı ok, hata ayıklayıcının şu anda nerede duraklatılmış olduğunu gösterir.

## <a name="step-in-and-out-of-native-code"></a>Yerel kodun içinde ve dışında adım adım

1. Hata ayıklama yönetilen uygulamada duraklatılırken **F11** tuşuna basın veya Hata Ayıkla **adımını**  >  **seçin.**

   *Mixed_Mode.h* yerel üst bilgi dosyası açılır ve hata ayıklayıcının duraklatılmış olduğu sarı oku görüyorsunuz.

   ![Yerel koda adımla](../debugger/media/mixed-mode-step-into-native-code.png)

1. Artık kesme noktaları ayarp isabet ediyor ve yerel veya yönetilen kodda değişkenleri inceleyebilirsiniz.

   - Değerlerini görmek için kaynak kodundaki değişkenlerin üzerine gelin.

   - Otomatikler ve Yereller pencerelerinde **değişkene ve** **değerlerine** bakın.

   - Hata ayıklayıcıda duraklatılmışken, İzleme pencerelerini ve **Çağrı** Yığını penceresini **de kullanabilirsiniz.**

1. Hata ayıklayıcıyı bir satır ilerlemek için **F11** tuşuna basın.

1.  + Yürütmeye devam etmek için SHIFT **F11** tuşuna basın veya **hata ayıklama**  >  **adımını** seçin seçeneğini belirleyin.

1. Uygulamada hata ayıklamaya devam etmek için **F5** tuşuna basın veya yeşil oku seçin.

Tebrikler! Karışık modda hata ayıklama öğreticisini tamamladınız.

## <a name="next-step"></a>Sonraki adım

Bu öğreticide, karışık modda hata ayıklamayı etkinleştirerek, yönetilen bir uygulamadaki yerel kodun hatalarını ayıklamanın nasıl yapılacağını öğrendiniz. Diğer hata ayıklayıcı özelliklerine genel bakış için bkz.:

> [!div class="nextstepaction"]
> [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
