---
title: Gelişmiş derleme ayarları Iletişim kutusu (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 38f4d233c8804bec91d2f7dfd2dc34c6879e8be9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651729"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Gelişmiş Derleme Ayarları İletişim Kutusu (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Projenin Gelişmiş derleme yapılandırma özelliklerini belirtmek için **Proje Tasarımcısı** ' nın **Advancedbuild ayarları** iletişim kutusunu kullanın. Bu iletişim kutusu [!INCLUDE[csprcs](../../includes/csprcs-md.md)] yalnızca projeler için geçerlidir.

## <a name="general"></a>Genel
 Aşağıdaki seçenekler genel Gelişmiş ayarları ayarlamanıza olanak sağlar.

 **Dil sürümü** Kullanılacak dilin sürümünü belirtir. Özellik kümesi her sürümde farklıdır, bu nedenle derleyicinin uygulanan özelliklerin yalnızca bir alt kümesine izin vermeye zorlamak veya yalnızca var olan bir standartta uyumlu özellikleri etkinleştirmek için bu seçenek kullanılabilir. Bu ayar aşağıdaki seçeneklere sahiptir:

- **ISO-1**

   ISO-1 Standart özelliklerini hedefler.

- **default**

   Geçerli sürümü hedefler.

  Daha fazla bilgi için bkz. [/langversion (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).

  **Iç derleyici hata bildirimi** Derleyici hatalarının Microsoft 'a raporlanıp raporlanmayacağını belirtir. **İstem** olarak ayarlandıysa (varsayılan), iç derleyici hatası oluşursa, Microsoft 'a elektronik bir hata raporu gönderme seçeneği sunarak bir istem alırsınız. **Send**olarak ayarlandıysa, otomatik olarak bir hata raporu gönderilir. **Sıraya**ayarlandıysa, hata raporları sıraya alınır. **None**olarak ayarlanırsa, hata yalnızca derleyicinin metin çıkışında bildirilir. Daha fazla bilgi için bkz. [/errorreport (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).

  **Aritmetik taşma/yetersiz kalması Için denetle** [Checked](https://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) veya [unchecked](https://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) anahtar kelimelerinde bulunmayan ve veri türü aralığının dışında bir değer elde eden bir tamsayı aritmetik ifadesinin çalışma zamanı özel durumuna neden olup olmayacağını belirtir. Daha fazla bilgi için bkz. [/checked (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).

  **Başvuruya mscorlib.dll** mscorlib.dll, tüm ad alanını tanımlayarak, programınıza içeri aktarılmayacağını belirtir <xref:System> . Kendi ad alanınızı ve nesnelerinizi tanımlamak veya oluşturmak istiyorsanız bu kutuyu işaretleyin <xref:System> . Daha fazla bilgi için bkz. [/nostdlib (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).

## <a name="output"></a>Çıktı
 Aşağıdaki seçenekler gelişmiş çıkış seçeneklerini belirtmenizi sağlar.

 **Hata ayıklama bilgileri** Derleyici tarafından oluşturulan hata ayıklama bilgilerinin türünü belirtir. Bir uygulamanın hata ayıklama performansını yapılandırma hakkında daha fazla bilgi için bkz. [bir görüntüyü hata ayıklamayı kolaylaştırın](https://msdn.microsoft.com/library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3). Bu ayar aşağıdaki seçeneklere sahiptir:

- **yok**

   Hata ayıklama bilgilerinin üretilmeyecek olduğunu belirtir

- **tümünü**

   Çalışan programa hata ayıklayıcı iliştirmesini sağlar.

- **pdbonly**

   Program hata ayıklayıcıda başlatıldığında kaynak kodu hata ayıklamasına izin verir, ancak çalışan program hata ayıklayıcıya eklendiğinde yalnızca assembler görüntülenir.

  Daha fazla bilgi için bkz. [/Debug (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).

  **Dosya hizalaması** Çıkış dosyasındaki bölümlerin boyutunu belirtir. Geçerli değerler **512**, **1024**, **2048**, **4096**ve **8192**. Bu değerler bayt cinsinden ölçülür. Her bölüm, çıkış dosyasının boyutunu etkileyen bu değerin birden çok katı olan bir sınıra göre hizalanacaktır. Daha fazla bilgi için bkz. [/filealign (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).

  **Dll taban adresi** DLL 'nin yükleneceği tercih edilen temel adresi belirtir. Bir DLL için varsayılan temel adres, [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ortak dil çalışma zamanı tarafından ayarlanır. Daha fazla bilgi için bkz. [/BaseAddress (C# derleyici seçenekleri)](https://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).

## <a name="see-also"></a>Ayrıca Bkz.
 [C# derleyici seçenekleri](https://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44) [derleme sayfası, proje Tasarımcısı (c#)](../../ide/reference/build-page-project-designer-csharp.md)
