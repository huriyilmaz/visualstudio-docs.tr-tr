---
title: Kaynak denetimi eklentileri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5a99ebdf2366ce6a60a6a724afc7d742db7150f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705799"
---
# <a name="source-control-plug-ins"></a>Kaynak Denetimi Eklentileri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kaynak denetimi eklentisi SDK 'Sı başvuru bölümü, kaynak denetim sistemlerinin ile tümleştirilebilmesine olanak tanıyan tam arabirim belirtimini içerir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Kaynak denetim eklentisinin [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tümleşik geliştirme ortamı (IDE) ile arabirim için uygulanması gereken çeşitli işlevlerin ve veri türlerinin söz dizimi ve semantiğini belirtir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Kaynak Denetimi Eklentisi API İşlevleri](../extensibility/source-control-plug-in-api-functions.md)  
 Kaynak denetimi eklentisi API 'siyle uyum sağlamak için kaynak denetim eklentisi tarafından uygulanması gereken işlevleri listeler.  
  
 [IDE Tarafından Uygulanan Geri Çağırma İşlevleri](../extensibility/callback-functions-implemented-by-the-ide.md)  
 Kaynak denetimi eklentisinin, belirli komutlar yürütüldüğü sırada bilgileri IDE 'ye geri iletmek için kullandığı işlevleri açıklar.  
  
 [Numaralandırıcılar](../extensibility/enumerators.md)  
 Kaynak denetimi eklentisinin hakkında bilgi sahibi olması gereken kaynak denetimi eklentisi API 'sindeki Numaralandırıcı veri türlerini listeler.  
  
 [Özellik Bayrakları](../extensibility/capability-flags.md)  
 `SCC_CAP_xxx`Bir sağlayıcının yeteneklerini belirten bayrakları açıklar.  
  
 [Özel Komutlar Tarafından Kullanılan Bit Bayrakları](../extensibility/bitflags-used-by-specific-commands.md)  
 Belirli komutlar bağlamında yararlı olan bayrakları listeler.  
  
 [Hata Kodları](../extensibility/error-codes.md)  
 İşlevleri tarafından döndürülen yaygın hata değerlerini listeler `SCCTRN` .  
  
 [Kaynak Denetimi Eklentisi Bulmak için Anahtar Olarak Kullanılan Dizeler](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 Kaynak denetimi eklentisini bulmak için kayıt defterine erişim anahtarlarını açıklar.  
  
 [MSSCCPRJ.SCC Dosyası](../extensibility/mssccprj-scc-file.md)  
 IDE 'de donuk bilgiler içeren, ancak sürüm denetimindeki çözümü veya projeyi bulmak için kaynak denetim eklentisi tarafından kullanılan bir istemci tarafı dosyayı açıklar.  
  
 [Kaynak Denetimi Eklentisi Uygulamak için En İyi Yöntemler](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Kaynak denetimi eklentisi API 'SI uygulanırken dikkat etmeniz gereken önemli bir teknik anımsatıcı koleksiyonu sağlar.  
  
 [Dize Uzunluğu Kısıtlamaları](../extensibility/restrictions-on-string-lengths.md)  
 Çeşitli işlevlerde kullanılan dizelerin uzunluklarıyla kaynak denetimi eklentisi API 'sindeki sınırlamaları açıklar.  
  
 [Sözlük](../extensibility/source-control-plug-in-glossary.md)  
 Kaynak denetimi eklentisi SDK belgelerini okumak için faydalı terimler ve bunların tanımlarını sağlar.  
  
 [Nasıl Yapılır: Kaynak Denetimi Eklentileri için Uyumluluk Uyarılarını Kapatma](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Uyarıların nasıl devre dışı bırakılacağını açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Kaynak denetimi eklentisi örneği](https://msdn.microsoft.com/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 Kaynak denetimi eklentisi işlevlerinin bir örneğini sağlar.  
  
 [Kaynak Denetimi Eklentileri için Test Kılavuzu](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Kaynak denetimi eklentisiyle ilgili test yordamlarını açıklar.  
  
 [Kaynak Denetimi Eklentisi Oluşturma](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Kaynak denetimi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Kullanıcı arabirimini (UI) kullanırken kaynak denetimi işlevselliği sağlayan bir kaynak denetimi eklentisinin nasıl oluşturulacağını açıklar.  
  
 [Visual Studio SDK Başvurusu](../extensibility/visual-studio-sdk-reference.md)  
 Başvuru konularının bir listesini gösterir.
