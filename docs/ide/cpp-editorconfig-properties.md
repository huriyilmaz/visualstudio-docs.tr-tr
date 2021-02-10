---
title: C++ EditorConfig biçimlendirme kuralları
titleSuffix: ''
description: Visual Studio 'da C++ kodunu biçimlendirmek için EditorConfig 'in nasıl kullanılacağı hakkında bilgi edinin.
ms.date: 9/14/2020
author: jureid
ms.author: jureid
manager: jmartens
dev_langs:
- CPP
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- cplusplus
monikerRange: vs-2019
ms.openlocfilehash: 490a7b29d6e3d8a2dc63c27b9e9d7226b5d22662
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970887"
---
# <a name="c-editorconfig-formatting-conventions"></a>C++ EditorConfig biçimlendirme kuralları

Visual Studio C++ biçimlendiricisi, genel olarak uygulanabilen, zengin bir yapılandırılabilir ayarlar kümesine sahiptir. Belirli bir çalışma alanının C++ biçimlendirme ayarlarını ayarlamak için [clangformat](https://clang.llvm.org/docs/ClangFormat.html) veya [editorconfig](https://editorconfig.org/)kullanın. Hem Visual Studio hem de Visual Studio Code, genel Visual Studio C++ biçimlendirme ayarlarının her biri için yerleşik EditorConfig desteğine sahiptir ve bu da EditorConfig ayarları önceliklidir. Bu, C++ biçimlendirmesini daha ayrıntılı bir düzeyde yapılandırmak ve projeye katkıda bulunan herkes için tutarlı kod stili uygulamak üzere çalışma alanınıza EditorConfig dosyaları ekleyebileceğiniz anlamına gelir.

## <a name="c-formatting-conventions"></a>C++ biçimlendirme kuralları

C++ biçimlendirme EditorConfig ayarları ön ekine sahiptir `cpp_` . Aşağıda, EditorConfig dosyanızın nasıl görünebileceğini bir örnek verilmiştir:

```ini
[*.{c++,cc,cpp,cxx,h,h++,hh,hpp,hxx,inl,ipp,tlh,tli}]

cpp_indent_case_contents_when_block = true
cpp_new_line_before_open_brace_namespace = same_line
```

Bu belgenin geri kalanında, Visual Studio ve VS Code tarafından desteklenen tüm EditorConfig C++ biçimlendirme ayarları listelenir.

### <a name="indentation-settings"></a>Girintileme ayarları

**Girinti ayraçları**

- Ad: `cpp_indent_braces`
- Değerler: `true` , `false`

**Her satırı göreceli olarak Girintile**

- Ad: `cpp_indent_multi_line_relative_to`
- Değerler:
  - `outermost_parenthesis` -Yeni bir satır yazıldığında, göreceli olarak en dıştaki açık ayraçla girintilenir.
  - `innermost_parenthesis` -Yeni bir satır yazıldığında, bu, en içteki açık ayraçla göreli olarak girintilenir.
  - `statement_begin` -Yeni bir satır yazıldığında, geçerli deyimin başına göreli olarak girintilenir.

**Parantez içinde, yeni satırları yazdığımda Hizala**

- Ad: `cpp_indent_within_parentheses`
- Değerler:
  - `align_to_parenthesis` -Parantez açmak için içeriği hizalayın.
  - `indent` -Yeni satırları Girintile.

**Mevcut kodda, parantez içindeki yeni satırların hizalaması için ayarı kullanmayın**

- Ad: `cpp_indent_preserve_within_parentheses`
- Değerler: `true` , `false`

**Büyük/küçük harf içeriğini Girintile**

- Ad: `cpp_indent_case_contents`
- Değerler: `true` , `false`

**Büyük/küçük harf etiketlerini Girintile**

- Ad: `cpp_indent_case_labels`
- Değerler: `true` , `false`

**Case deyiminden sonra ayraçları Girintile**

- Ad: `cpp_indent_case_contents_when_block`
- Değerler: `true` , `false`

**Parametre olarak kullanılan lambdaların ayraçlarını Girintile**

- Ad: `cpp_indent_lambda_braces_when_parameter`
- Değerler: `true` , `false`

**Goto etiketlerinin konumu**

- Ad: `cpp_indent_goto_labels`
- Değerler:
  - `one_left` -Sola bir girinti
  - `leftmost_column` -En soldaki sütuna taşı
  - `none` -Girintili kalsın

**Önişlemci yönergelerinin konumu**

- Ad: `cpp_indent_preprocessor`
- Değerler:
  - `one_left` -Sola bir girinti
  - `leftmost_column` -En soldaki sütuna taşı
  - `none` -Girintili kalsın

**Erişim belirticilerini Girintile**

- Ad: `cpp_indent_access_specifiers`
- Değerler: `true` , `false`

**Ad alanı içeriklerini Girintile**

- Ad: `cpp_indent_namespace_contents`
- Değerler: `true` , `false`

**Yorumların girintilenmesini koru**

- Ad: `cpp_indent_preserve_comments`
- Değerler: `true` , `false`

### <a name="newline-settings"></a>Yeni satır ayarları

**Ad alanları için açık küme ayraçlarının konumu**

- Ad: `cpp_new_line_before_open_brace_namespace`
- Değerler:
  - `new_line` -Yeni bir satıra taşı
  - `same_line` -Aynı satırda tutun, ancak daha önce bir boşluk ekleyin
  - `ignore` -Otomatik olarak yeniden Konumlandır

**Türler için açık küme ayraçlarının konumu**

- Ad: `cpp_new_line_before_open_brace_type`
- Değerler:
  - `new_line` -Yeni bir satıra taşı
  - `same_line` -Aynı satırda tutun, ancak daha önce bir boşluk ekleyin
  - `ignore` -Otomatik olarak yeniden Konumlandır

**İşlevler için açık küme ayraçlarının konumu**

- Ad: `cpp_new_line_before_open_brace_function`
- Değerler:
  - `new_line` -Yeni bir satıra taşı
  - `same_line` -Aynı satırda tutun, ancak daha önce bir boşluk ekleyin
  - `ignore` -Otomatik olarak yeniden Konumlandır

**Denetim blokları için açık küme ayraçlarının konumu**

- Ad: `cpp_new_line_before_open_brace_block`
- Değerler:
  - `new_line` -Yeni bir satıra taşı
  - `same_line` -Aynı satırda tutun, ancak daha önce bir boşluk ekleyin
  - `ignore` -Otomatik olarak yeniden Konumlandır

**Lambdalar için açık küme ayraçlarının konumu**

- Ad: `cpp_new_line_before_open_brace_lambda`
- Değerler:
  - `new_line` -Yeni bir satıra taşı
  - `same_line` -Aynı satırda tutun, ancak daha önce bir boşluk ekleyin
  - `ignore` -Otomatik olarak yeniden Konumlandır
 
**Kapsam ayraçları ayrı satırlara yerleştir**

- Ad: `cpp_new_line_scope_braces_on_separate_lines`
- Değerler: `true` , `false`

**Boş türler için, kapatma küme ayraçlarını açma küme ayraçlarıyla aynı satıra taşıyın**

- Ad: `cpp_new_line_close_brace_same_line_empty_type`
- Değerler: `true` , `false`

**Boş işlev gövdeleri için, kapatma küme ayraçlarını açma küme ayraçlarıyla aynı satıra taşıyın**

- Ad: `cpp_new_line_close_brace_same_line_empty_function`
- Değerler: `true` , `false`

**' Catch ' ve benzer anahtar sözcükleri yeni bir satıra yerleştir**

- Ad: `cpp_new_line_before_catch`
- Değerler: `true` , `false`

**' Else ' öğesini yeni bir satıra yerleştir**

- Ad: `cpp_new_line_before_else`
- Değerler: `true` , `false`

**Do-while döngüsünde yeni bir satıra ' while ' yerleştir**

- Ad: `cpp_new_line_before_while_in_do_while`
- Değerler: `true` , `false`

### <a name="spacing-settings"></a>Aralık ayarları

**İşlev adları ve bağımsız değişken listelerinin açılış ayraçları arasındaki boşluk**

- Ad: `cpp_space_before_function_open_parenthesis`
- Değerler:
  - `insert` -Bir boşluk ekleyin
  - `remove` -Boşlukları kaldır
  - `ignore` -Boşlukları değiştirme

**Bağımsız değişken listesinin parantezleri içine boşluk Ekle**

- Ad `cpp_space_within_parameter_list_parentheses` değerleri: `true` , `false`

**Bağımsız değişken listesi boş olduğunda parantezler arasında boşluk Ekle**

- Ad: `cpp_space_between_empty_parameter_list_parentheses`
- Değerler: `true` , `false`

**Denetim akışı deyimlerinde anahtar sözcük ve açma ayracı arasına boşluk Ekle**

- Ad: `cpp_space_after_keywords_in_control_flow_statements`
- Değerler: `true` , `false`

**Denetim ifadesinin parantezleri içinde boşluk Ekle**

- Ad: `cpp_space_within_control_flow_statement_parentheses`
- Değerler: `true` , `false`

**Lambda bağımsız değişken listelerinin açılış ayracından önce boşluk Ekle**

- Ad: `cpp_space_before_lambda_open_parenthesis`
- Değerler: `true` , `false`

**C stili tür dönüştürmenin parantezleri içinde boşluk Ekle**

- Ad: `cpp_space_within_cast_parentheses`
- Değerler: `true` , `false`

**C stili tür dönüştürmenin kapatma parantezinden sonra boşluk Ekle**

- Ad: `cpp_space_after_cast_close_parenthesis`
- Değerler: `true` , `false`

**Parantez içine alınmış bir ifadenin parantezleri içinde boşluk Ekle**

- Ad: `cpp_space_within_expression_parentheses`
- Değerler: `true` , `false`

**Blok ayracını açmadan önce boşluk Ekle**

- Ad: `cpp_space_before_block_open_brace`
- Değerler: `true` , `false`

**Boş küme ayraçları arasında boşluk Ekle**

- Ad: `cpp_space_between_empty_braces`
- Değerler: `true` , `false`

**Tek düzen başlatma ve Başlatıcı listelerinin ayracını açmadan önce boşluk Ekle**

- Ad: `cpp_space_before_initializer_list_open_brace`
- Değerler: `true` , `false`

**Tek düzen başlatma ve Başlatıcı listelerinin küme ayraçları içine boşluk Ekle**

- Ad: `cpp_space_within_initializer_list_braces`
- Değerler: `true` , `false`

**Tek düzen başlatma ve başlatıcı listeleri içindeki boşlukları koru**

- Ad: `cpp_space_preserve_in_initializer_list`
- Değerler: `true` , `false`

**Açma köşeli ayracından önce boşluk Ekle**

- Ad: `cpp_space_before_open_square_bracket`
- Değerler: `true` , `false`

**Köşeli ayraç içine boşluk Ekle**

- Ad: `cpp_space_within_square_brackets`
- Değerler: `true` , `false`

**Boş köşeli ayraçlardan önce boşluk Ekle**

- Ad: `cpp_space_before_empty_square_brackets`
- Değerler: `true` , `false`

**Boş köşeli ayraç arasına boşluk Ekle**

- Ad: `cpp_space_between_empty_square_brackets`
- Değerler: `true` , `false`

**Çok boyutlu diziler için köşeli ayraçları Gruplandır**

- Ad: `cpp_space_group_square_brackets`
- Değerler: `true` , `false`

**Lambdalar için köşeli ayraç içine boşluk Ekle**

- Ad: `cpp_space_within_lambda_brackets`
- Değerler: `true` , `false`

**Spacebetweenemptylambdavköşeli ayraç**

- Ad: `cpp_space_between_empty_lambda_brackets`
- Değerler: `true` , `false`

**Virgüllerden önce boşluk Ekle**

- Ad: `cpp_space_before_comma`
- Değerler: `true` , `false`

**Virgüllerden sonra boşluk Ekle**

- Ad: `cpp_space_after_comma`
- Değerler: `true` , `false`

**Üye işleçlerden önce ve sonra boşlukları kaldır**

- Ad: `cpp_space_remove_around_member_operators`
- Değerler: `true` , `false`

**Tür bildirimlerinde taban için iki noktadan önce boşluk Ekle**

- Ad: `cpp_space_before_inheritance_colon`
- Değerler: `true` , `false`

**Oluşturucular için iki noktadan önce boşluk Ekle**

- Ad: `cpp_space_before_constructor_colon`
- Değerler: `true` , `false`

**Noktalı virgüllerden önce boşluğu kaldır**

- Ad: `cpp_space_remove_before_semicolon`
- Değerler: `true` , `false`

**Noktalı virgülden sonra boşluk Ekle**

- Ad: `cpp_space_after_semicolon`
- Değerler: `true` , `false`

**Birli İşleçler ve işlenenleri arasındaki boşlukları kaldır**

- Ad: `cpp_space_remove_around_unary_operator`
- Değerler: `true` , `false`

**İkili işleçler için boşluk**

- Ad: `cpp_space_around_binary_operator`
- Değerler:
  - `insert` -İkili işleçlerden önce ve sonra boşluk ekleyin.
  - `remove` -İkili operatörlerin çevresindeki boşlukları kaldırın.
  - `ignore` -İkili operatörlerin çevresindeki boşlukları değiştirmeyin.

**Atama işleçleri için boşluk**

- Ad: `cpp_space_around_assignment_operator`
- Değerler:
  - `insert` -Atama işleçleri etrafına boşluk ekleyin.
  - `remove` -Atama işleçleri etrafında boşlukları kaldırın.
  - `ignore` -Atama işleçleri etrafında boşluk değiştirmeyin.

**İşaretçi/başvuru hizalaması**

- Ad: `cpp_space_pointer_reference_alignment`
- Değerler:
  - `left` -Sola Hizala.
  - `center` -Dikey Ortala.
  - `right` -Sağa hizalayın.
  - `ignore` -Değiştirilmeden bırakın.

**Koşullu işleçler için boşluk**

- Ad: `cpp_space_around_ternary_operator`
- Değerler:
  - `insert` -Koşullu operatörlerin etrafına boşluk ekleyin.
  - `remove` -Koşullu operatörlerin çevresindeki boşlukları kaldırın.
  - `ignore` -Koşullu operatörlerin çevresindeki boşlukları değiştirmeyin.

### <a name="wrapping-options"></a>Kaydırma seçenekleri

**Bloklar için kaydırma seçenekleri**

- Ad: `cpp_wrap_preserve_blocks`
- Değerler:
  - `one_liners` -Tek satırlık kod bloklarını sarmayın.
  - `all_one_line_scopes` -Açılış ve kapanış ayraçları bir sonraki satırda olduğunda kod bloklarını sarmayın.
  - `never` -Bloklar için her zaman yeni satır ayarları uygulayın.

## <a name="see-also"></a>Ayrıca bkz.

- [EditorConfig.org](https://editorconfig.org/)
- [Dil hizmeti için EditorConfig destekleme](../extensibility/supporting-editorconfig.md)
- [Kod düzenleyicisinin özellikleri](writing-code-in-the-code-and-text-editor.md)
