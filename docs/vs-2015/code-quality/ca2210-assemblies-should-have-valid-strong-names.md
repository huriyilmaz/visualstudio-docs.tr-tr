---
title: 'CA2210: derlemeler geçerli tanımlayıcı adlara sahip olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6109e0dc18f98d0b22dfb5c548bd12447b53e61d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662990"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: Derlemelerin tanımlayıcı adı geçerli olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bütünleştirilmiş kod bir tanımlayıcı ad ile imzalanmamıştır, tanımlayıcı ad doğrulanamadı veya tanımlayıcı ad bilgisayarın geçerli kayıt defteri ayarları olmadan geçerli değildir.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, bir derlemenin tanımlayıcı adını alır ve doğrular. Aşağıdakilerden biri doğruysa bir ihlal oluşur:

- Derlemenin tanımlayıcı adı yok.

- İmza, imzalandıktan sonra değiştirildi.

- Derleme gecikmeli imzalanmış.

- Derleme yanlış imzalanmış veya imzalama başarısız oldu.

- Derleme için kayıt defteri ayarlarının doğrulanması gerekir. Örneğin, tanımlayıcı ad Aracı (sn. exe), derleme için doğrulamayı atlamak için kullanılır.

  Güçlü ad oynanmış derlemeyi bilmeden yükleyerek istemcileri korur. Güçlü adı olmayan derlemeler oldukça sınırlı sayıda senaryo dışında kullanılmamalıdır. Düzgün imzalanmamış derlemeleri paylaşırsanız veya dağıtırsanız, derleme aslı bozuabilir, ortak dil çalışma zamanı derlemeyi yükleyemeyebilir veya kullanıcı kendi bilgisayarındaki doğrulamayı devre dışı bırakabilir. Güçlü adı olmayan bir derleme aşağıdaki dezavantajlardan daha fazlasını içerir:

- Kaynakları doğrulanamıyor.

- Ortak dil çalışma zamanı, derlemenin içeriği değiştirilmişse kullanıcıları uyaramaz.

- Genel bütünleştirilmiş kod önbelleğine yüklenemez.

  Gecikmeli imzalanmış bir derlemeyi yüklemek ve analiz etmek için, derlemenin doğrulanmasını devre dışı bırakmanız gerektiğini unutmayın.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 **Anahtar dosyası oluşturmak için**

 Aşağıdaki yordamlardan birini kullanın:

- @No__t_0 SDK tarafından sunulan derleme bağlayıcı aracı 'nı (al. exe) kullanın.

- @No__t_0 v 1.0 veya v 1.1 için <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> veya <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> özniteliğini kullanın.

- @No__t_0 için `/keyfile` veya `/keycontainer` derleyici seçeneği [/keyfile (bir derlemeyi imzalamak Için anahtar veya anahtar çiftini belirtin)](https://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06) veya [/keycontainer (bir derlemeyi Imzalamak Için anahtar kapsayıcısı belirtin)](https://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e) ' deki C++bağlayıcı seçeneğini kullanın.

  **Derlemenizi Visual Studio 'da güçlü bir adla imzalamak için**

1. @No__t_0, çözümünüzü açın.

2. **Çözüm Gezgini**, projenize sağ tıklayın ve ardından Özellikler ' e tıklayın **.**

3. **İmzalama** sekmesine tıklayın ve **derlemeyi imzala** onay kutusunu seçin.

4. **Bir tanımlayıcı ad anahtar dosyası seçin**listesinden **Yeni**' yi seçin.

    **Tanımlayıcı ad oluştur anahtar** penceresi görüntülenecektir.

5. **Anahtar dosya adı**' nda, tanımlayıcı ad anahtarınız için bir ad yazın.

6. Anahtarın bir parolayla korunmasını seçin ve ardından **Tamam**' a tıklayın.

7. **Çözüm Gezgini**, projenize sağ tıklayın ve ardından **Oluştur**' a tıklayın.

   **Derlemenizi Visual Studio dışında güçlü bir adla imzalamak için**

- @No__t_0 SDK tarafından sunulan tanımlayıcı ad aracı 'nı (sn. exe) kullanın. Daha fazla bilgi için bkz. [sn. exe (tanımlayıcı ad aracı)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6).

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan yalnızca derleme, içerik üzerinde değişiklik yapılmasını gerektiren bir ortamda kullanılıyorsa bir uyarı göstermez.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName><xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
 [Nasıl yapılır: bir derlemeyi tanımlayıcı ad](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [sn. exe Ile Imzalama (tanımlayıcı ad aracı)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)
