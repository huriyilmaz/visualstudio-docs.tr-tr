---
title: Eski dil Service2 kaydetme | Microsoft Docs
description: Bu makalede Visual Studio ' de kullanılabilen çeşitli dil hizmeti seçenekleri için kayıt defteri girişleri listelenmektedir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d33ce0af87df2e3d6506fef48aeb91f1b9ebdeef
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062968"
---
# <a name="registering-a-legacy-language-service-2"></a>Eski dil hizmeti kaydetme 2
Aşağıdaki bölümler, ' de kullanılabilen çeşitli dil hizmeti seçenekleri için kayıt defteri girişlerinin listesini sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Aşağıdaki kayıt defteri girdileri listesinde, *vs reg Root* HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *x. y* değerine eşittir; burada *x. y* [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sürüm numarasıdır.

## <a name="registry-entries-for-language-service-options"></a>Dil hizmeti seçenekleri için kayıt defteri girişleri
 *Vs reg root*\ Languages\language Services \\ *dil adı* anahtarı aşağıdaki değerleri içerebilir.

|Ad|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ|*\<GUID>*|Dil hizmetinin GUID 'SI.|
|Dil dili|REG_DWORD|0x0-0xFFFF|Dilin yerelleştirilmiş metin adı için dize kaynak tanımlayıcısı (resd).|
|Paket|REG_SZ|*\<GUID>*|VSPackage GUID 'SI.|
|ShowCompletion|REG_DWORD|0-1|**Seçenekler** Iletişim kutusundaki **deyimin tamamlama** seçeneklerinin etkinleştirilip etkinleştirilmeyeceğini belirtir.|
|Showsmartgirintile|REG_DWORD|0-1|**Seçenekler** Iletişim kutusunda **akıllı** girintileme seçme seçeneğinin etkinleştirilip etkinleştirilmediğini belirtir.|
|RequestStockColors|REG_DWORD|0-1|Özel veya varsayılan renklerin anahtar sözcükleri renklendirmek için kullanılıp kullanılmayacağını belirtir.|
|ShowHotURLs|REG_DWORD|0-1|Kullanıcının URL 'ye tıklayıp tıklaamayacağını belirtir.|
|Varsayılan değer, etkin olmayan URL 'Ler|REG_DWORD|0-1|**Seçenekler** iletişim kutusunda **tek tıklama URL 'si gezintisini etkinleştir** seçeneğinin başlangıç ayarını belirtir.|
|Defaulttoınsertspaces|REG_DWORD|0-1|Dil hizmetinin varsayılan sekme seçeneği olarak "boşluk Ekle" olup olmadığını belirtir.|
|ShowDropdownBarOption|REG_DWORD|0-1|**Gezinti çubuğunu** gösteren veya gizleyen **Seçenekler** iletişim kutusunda **Gezinti çubuğu** seçeneğini sunar veya devre dışı bırakır.|
|Yalnızca tek kod penceresi|REG_DWORD|0-1|Dil hizmeti için **pencere** menüsündeki **yeni pencere** seçeneğini devre dışı bırakır veya devre dışı bırakır.|
|EnableAdvancedMembersOption|REG_DWORD|0-1|**Gelişmiş üyeleri Gizle** Için bir **seçenek** iletişim kutusu ayarını etkinleştirilir veya devre dışı bırakır.|
|Destek CF_HTML|REG_DWORD|0-1|Düzenleyicinin HTML verilerinin kopyalanmasını ve yapıştırmasını etkinleştirilip etkinleştirilmeyeceğini belirtir.|
|EnableLineNumbersOption|REG_DWORD|0-1|**Seçenekler** Iletişim kutusundaki **satır numaraları** seçeneklerinin bir dil hizmeti için etkinleştirilip etkinleştirilmeyeceğini belirtir.|
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Özel alanlar gibi gelişmiş üyelerin tamamlanma listelerinde gizli olup olmadığını belirtir.|
|ShowBraceCompletion|REG_DWORD|0-1|**Seçenekler** Iletişim kutusunda **küme ayracı tamamlama** seçeneğinin etkin olup olmadığını belirtir.|

### <a name="example"></a>Örnek

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
        LangResID             = reg_dword:0x00000000
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}
        ShowCompletion        = reg_dword:0x00000001
        ShowSmartIndent       = reg_dword:0x00000001
        ShowDropdownBarOption = reg_dword:0x00000001
```

## <a name="registry-entries-for-debugger-languages-options"></a>Hata ayıklayıcı dilleri için kayıt defteri girişleri seçenekleri
 *Vs reg root*\Languages\language Services \\ *dil adı*\debugger dilleri \\ *GUID*\ Key aşağıdaki değerleri içerebilir.

|Ad|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ|metin|Varsayılan değer dilin adını belgelemek için kullanılabilir. Bu anahtarın adı, \Ad7metrics\expression değerlendirici içinde karşılık gelen bir girişe sahip bir ifade değerlendirici GUID 'sidir *\<VS Reg Root>* .|

### <a name="example"></a>Örnek

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        Debugger Languages\
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\
            (Default) = reg_sz:C++
```

## <a name="registry-entries-for-editor-tools-options"></a>Düzenleyici araçları seçenekleri için kayıt defteri girişleri
 Özellik sayfaları ve özellik düğümleri için Editoraraçları seçenekler anahtarının altına kayıt defteri anahtarları ekleyebilirsiniz. Bu anahtarlar ve değerleri, dil hizmetini yapılandırmak için kullanılan **Seçenekler** iletişim kutusundaki ( **Araçlar** menüsünde) özellik sayfalarını belirler. Aşağıdaki örnekte, *sayfa adı* bir özellik sayfasının adıdır ve *düğüm adı* , **Seçenekler** iletişim kutusundaki ağaçtaki bir düğümün adıdır. Sayfa girişi ve düğüm girdisi ayrı olarak belirtilmelidir.

|Ad|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ|RESID|Bu seçenek sayfasının yerelleştirilmiş görünen adı. Ad, `nnn` `nnn` belirtilen VSPackage 'ın uydu dll 'sinde bir DIZE kaynak kimliği olan harflerden oluşan bir metin veya # olabilir.|
|Paket|REG_SZ|*'INI*|Bu seçenekler sayfasını uygulayan VSPackage GUID 'ı.|
|Sayfa|REG_SZ|*'INI*|Yöntemi çağırarak VSPackage 'dan istek yapılacak Özellik sayfasının GUID 'ı <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> . Bu kayıt defteri girdisi yoksa, kayıt defteri anahtarı bir sayfayı değil, bir düğümü tanımlar.|

### <a name="example"></a>Örnek

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      CSharp\
        EditorToolsOptions\
          Formatting\
            (Default) = reg_sz:#242
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
            General\
              (Default) = reg_sz:#255
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}
            Indentation\
              (Default) = reg_sz:#250
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}
            Newlines\
              (Default) = reg_sz:#253
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}
```

## <a name="registry-entries-for-file-name-extension-options"></a>Dosya adı uzantısı seçenekleri için kayıt defteri girişleri
 Dosya uzantısının girdisi, ". myext" gibi önde gelen süreyi içermelidir.

|Ad|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ|*'INI*|Bu dosya adı uzantısı türü için varsayılan dil hizmeti için hizmet GUID 'SI.|

### <a name="example"></a>Örnek

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>Düzenleyici seçenekleri için kayıt defteri girişleri
 *Vs reg root*\düzenleyiciler anahtarı aşağıdaki değerleri içerebilir:

|Ad|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ|""|Kullanılmayan belgelerinizi buraya yerleştirebilirsiniz.|
|DefaultToolboxTab|REG_SZ|""|Düzenleyici etkin olduğunda varsayılan hale getirmek için araç kutusu sekmesinin adı.|
|DisplayName|REG_SZ|RESID|**Birlikte Aç** iletişim kutusunda görüntülenecek ad. Ad, dize kaynak KIMLIĞI veya standart biçimdeki bir addır.|
|ExcludeDefTextEditor|REG_DWORD|0-1|**Birlikte Aç** menü komutu için kullanılır. Belirli bir dosya türü için kullanılabilir Düzenleyiciler listesinde varsayılan metin düzenleyiciyi listelemek istemiyorsanız, bu değeri 1 olarak ayarlayın.|
|LinkedEditorGUID|REG_SZ|*\<GUID>*|Kod sayfası desteğiyle bir dosyayı açan herhangi bir dil hizmeti için kullanılır. Örneğin, **birlikte Aç** komutunu kullanarak bir .txt dosyası açtığınızda, kaynak kodu düzenleyicisini kodlama olmadan kullanmak için seçenekler sağlanır.<br /><br /> Alt anahtarın adında belirtilen GUID, CodePage Düzenleyicisi fabrikası içindir; Bu belirli kayıt defteri girişinde belirtilen bağlı GUID, normal düzenleyici fabrikası içindir. Bu girdinin amacı, IDE 'nin varsayılan düzenleyiciyi kullanarak bir dosya açmadığından, IDE 'nin listedeki bir sonraki düzenleyiciyi kullanmayı deneyidir. Bu düzenleyici fabrikası temel olarak başarısız olan düzenleyici fabrikası ile aynı olduğundan, bu sonraki düzenleyici kod sayfası düzenleyici fabrikası olmamalıdır.|
|Paket|REG_SZ|*\<GUID>*|Görünen adın Restıd 'si için VSPackage GUID 'i.|

### <a name="example"></a>Örnek

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      (Default)            = reg_sz:Html Editor with Encoding
      DefaultToolboxTab    = reg_sz:HTML
      DisplayName          = reg_sz:#20101
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}
```

## <a name="registry-entries-for-logical-view-options"></a>Mantıksal Görünüm seçenekleri için kayıt defteri girişleri
 *Vs reg root*\Düzenleyiciler \\ *Düzenleyicisi GUI>* \logicalviews anahtarı aşağıdaki değerleri içerebilir.

|Ad|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ||Kullanılmıyor.|
|*\<GUID>*|REG_SZ|""|Desteklenen mantıksal görünümlere yönelik anahtar. İhtiyaç duyduğunuz kadar çok sayıda sahip olabilirsiniz. Kayıt defteri girişinin adı, her zaman boş bir dize olan değer değil önemli şeydir.|

### <a name="example"></a>Örnek

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      LogicalViews\
       (Default) = reg_sz:
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
```

## <a name="registry-entries-for-editor-extension-options"></a>Düzenleyici uzantısı seçenekleri için kayıt defteri girişleri
 *Vs reg root*\Düzenleyiciler \\ *Düzenleyicisi GUID*\Extensions anahtarı aşağıdaki değerleri içerebilir. Dosya adı uzantısı, önde gelen dönemi içermez.

|Ad|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|(Varsayılan)|REG_SZ||Kullanılmıyor.|
|*\<ext>*|REG_DWORD|0-0xFFFFFFFF|Uzantıların göreli önceliği. İki veya daha fazla dil aynı uzantıyı paylaşıyorsa, daha yüksek öncelikli dil seçilir.|

 Ayrıca, geçerli kullanıcının bir düzenleyici için varsayılan seçimi HKEY_Current_User \Software\Microsoft\VisualStudio \\ *X. Y*\ varsayılan düzenleyiciler EXT ' da depolanır \\ . Seçilen dil hizmetinin GUID 'SI özel girişte. Bu, geçerli kullanıcı için öncelik alır.

### <a name="example"></a>Örnek

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      Extensions\
       (Default) = reg_sz:
       *         = reg_dword:0x00000018
       html      = reg_dword:0x00000027
       shtm      = reg_dword:0x00000027
       shtml     = reg_dword:0x00000027
```

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Yönetilen paket çerçevesi dil hizmeti seçenekleri için kayıt defteri girişleri
 Aşağıdaki kayıt defteri girdileri, yönetilen paket çerçevesi (MPF) dil hizmeti sınıflarına özgüdür. Bu kayıt defteri girdileri, çeşitli IntelliSense özellikleri ve diğer gelişmiş Düzenle özellikleri için dil hizmetindeki desteği gösterir.

 Bu kayıt defteri girişlerine sınıfı aracılığıyla erişilir <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .

|Ad|Tür|Aralık|Açıklama|
|----------|----------|-----------|-----------------|
|CodeSense|REG_DWORD|0-1|IntelliSense işlemleri için destek.|
|Matchparantezleri|REG_DWORD|0-1|Ayraçlar, parantezler ve köşeli ayraçlar gibi eşleşen dil çiftleri için destek.|
|QuickInfo|REG_DWORD|0-1|IntelliSense Hızlı Bilgi işlemi desteği.|
|ShowMatchingBrace|REG_DWORD|0-1|Durum çubuğunda eşleşen dil çiftini görüntüleme desteği.|
|MatchBracesAtCaret|REG_DWORD|0-1|Eşleşen dil çiftlerini görüntüleme desteği, genellikle iki öğe vurgulanır.|
|MaxErrorMessages|REG_DWORD|0-n|Hata Listesi penceresinde görüntülenebilir maksimum **hata** sayısı.|
|CodeSenseDelay|REG_DWORD|0-n|IntelliSense işlemi için herhangi bir arka plan ayrıştırma işlemi başlatmadan önce geciktirilen milisaniye sayısı.|
|EnableAsyncCompletion|REG_DWORD|0-1|Arka plan ayrıştırma desteği.|
|EnableCommenting|REG_DWORD|0-1|Seçili metin bloklarını açıklamaya alma desteği ve ayrıca seçilen metnin açıklamalarını kaldırmak için destek anlamına gelir.|
|EnableFormatSelection|REG_DWORD|0-1|Otomatik girintileme veya ayraçların konumunu ayarlama gibi metin biçimlendirme desteği.|
|Otomatik Tamamlama|REG_DWORD|0-1|Altı çizili (daraltılmış bölgeler) desteği.|
|MaxRegions|REG_DWORD|0-n|Dosya başına en fazla gizli bölge sayısı.|

```
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      XML\
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}
        MatchBraces           = reg_dword:0x00000001
        QuickInfo             = reg_dword:0x00000001
        ShowMatchingBrace     = reg_dword:0x00000001
        MatchBracesAtCaret    = reg_dword:0x00000000
        MaxErrorMessages      = reg_dword:0x00000064
        CodeSenseDelay        = reg_dword:0x000001f4
        MaxRegions            = reg_dword:0x0000000a
```

## <a name="see-also"></a>Ayrıca bkz.
- [Eski Dil Hizmeti Geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)
