---
title: Derleme ve bildirim IMZALAMAYı yönetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 98d764bae48fb7deaa3f3cf917b0d4c8baab185b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651375"
---
# <a name="managing-assembly-and-manifest-signing"></a>Derleme ve Bildirim İmzalamayı Yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tanımlayıcı ad imzalama, bir yazılım bileşenine genel olarak benzersiz bir kimlik verir. Tanımlayıcı adlar, derlemenin başka bir kişi tarafından sızmasını sağlamak ve Bileşen bağımlılıkları ve yapılandırma deyimlerinin doğru bileşen ve bileşen sürümüyle eşleşmesini sağlamak için kullanılır.

 Güçlü bir ad, derlemenin kimliğinden (basit metin adı, sürüm numarası ve kültür bilgileri) ve bir ortak anahtar belirteci ve dijital imzadan oluşur.

 Visual Basic ve C# projelerinde derlemeleri imzalama hakkında daha fazla bilgi için, bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](https://msdn.microsoft.com/library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).

 Visual C++ projelerinde derlemeleri imzalama hakkında daha fazla bilgi için bkz. [tanımlayıcı ad derlemeleri (derleme imzalama) (C++/CLI)](https://msdn.microsoft.com/library/c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc).

## <a name="asset-types-and-signing"></a>Varlık türleri ve Imzalama
 .NET derlemelerini ve uygulama bildirimlerini imzalayabilirsiniz. Bu araçlar şunlardır:

- yürütülebilir dosyalar (. exe)

- uygulama bildirimleri (. exe. manifest)

- dağıtım bildirimleri (. Application)

- paylaşılan bileşen derlemeleri (. dll)

  Aşağıdaki varlık türlerini imzalamanız gerekir:

1. derlemeleri genel derleme önbelleği 'ne (GAC) dağıtmak istiyorsanız.

2. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama ve dağıtım bildirimleri. Visual Studio bu uygulamalar için varsayılan olarak imzalama imkanı sunar.

3. COM birlikte çalışabilirlik için kullanılan birincil birlikte çalışma derlemeleri. TLBIMP yardımcı programı bir COM tür kitaplığından birincil birlikte çalışma derlemesi oluştururken güçlü adlandırma uygular.

   Genel olarak, yürütülebilir dosyaları imzalayamamalıdır. Kesin adlı bir bileşen, uygulamayla dağıtılan, kesin olmayan adlandırılmış bir bileşene başvuramaz. Visual Studio uygulama yürütülebilir dosyalarını imzalamaz, bunun yerine zayıf adlı yürütülebiliri işaret eden uygulama bildirimini imzalar. İmzalama, bağımlılıkları yönetmeyi daha zor hale yapabileceğinden, genellikle uygulamanıza özel imza bileşenlerini kullanmaktan kaçının.

## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Visual Studio 'da bir derlemeyi Imzalama
 Proje Özellikleri penceresinin **imzalama** sekmesini kullanarak bir uygulamayı veya bileşeni imzalayabilirseniz ( **Çözüm Gezgini** proje düğümüne sağ tıklayıp **Özellikler**' i seçin veya **Hızlı başlat** penceresine **Proje ÖZELLIKLERI** yazın ya da **Çözüm Gezgini** penceresinin içinde alt + ENTER tuşlarına basın). **İmzalama** sekmesini seçin ve ardından **derlemeyi imzala** onay kutusunu seçin.

 Bir anahtar dosyası belirtin. Yeni bir anahtar dosyası oluşturmayı seçerseniz, yeni anahtar dosyalarının her zaman. pfx biçiminde oluşturulduğunu unutmayın. Yeni dosya için bir ad ve parola gerekir.

> [!WARNING]
> Başka birinin kullanmasını engellemek için anahtar dosyanızı her zaman bir parolayla korumanız gerekir. Ayrıca, sağlayıcıları veya sertifika depolarını kullanarak anahtarlarınızın güvenliğini sağlayabilirsiniz.

 Ayrıca zaten oluşturmuş olduğunuz bir anahtara işaret edebilirsiniz. Anahtar oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: genel-özel anahtar çifti oluşturma](https://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114).

 Yalnızca bir ortak anahtara erişiminiz varsa, anahtarın atanmasını ertelerseniz gecikme imzalamayı kullanabilirsiniz. **Yalnızca gecikmeli imzala** onay kutusunu seçerek gecikmeli imzalamayı etkinleştirin. Gecikmeli imzalanmış bir proje çalıştırılmaz ve hata ayıklayamazsınız. Ancak, [Sn.exe (tanımlayıcı ad aracı)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6) seçeneğini kullanarak, geliştirme sırasında doğrulamayı atlayabilirsiniz `-Vr` .

 Bildirimleri imzalama hakkında daha fazla bilgi için bkz. [nasıl yapılır: uygulama ve dağıtım bildirimlerini](../ide/how-to-sign-application-and-deployment-manifests.md)imzalama.

## <a name="see-also"></a>Ayrıca Bkz.
 [Tanımlayıcı adlı derlemeler](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b) [tanımlayıcı ad derlemeleri (derleme Imzalama) (C++/CLI)](https://msdn.microsoft.com/library/c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc)
