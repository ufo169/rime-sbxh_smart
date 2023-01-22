*变动比较多，没必要，不建议折腾*


rime.lua添加  
  topup_processor = require("jd27_topup")  
  date_translator = require("date")  
  
default.custom.yaml或sharedsupport/default.yaml  
  schema_list/+:  
    - schema: sbxh_smart  
    - schema: sbxh_stroke  
    - schema: pinyin   #依赖部署不了字典，可以添加方案部署后，再注释掉
方案选择：sbxh_smart  

# 「无码加词」，词库若含有编码，和系统词重码时置顶  
# 2字输入：s1y1s2y2b1b2  
# 3字输入：s1s2s3b1b2  
# 3字以上输入：s1s2s3s(end)b1b2  

data：（自己可以查看输入编码或修改）  
日期：orq  
时间：osj  
星期：oxq  
季节：ojj  

` 引导拼音反查  
i 引导重复上屏  
；引导快符输入  
\ 引导表情符号（输入编码可以查看mysymbols.yaml）  
o 引导符号输入（输入编码可以查看o_symbols.dict.yaml）  
' 引导手动造词  
如：'mooe'lia'nn	魔力鸟，空格上屏后，词组便可以按照规则打  
*注意中间的分隔符‘可以不要（'mooeliann）  

*注意：手动造词和自定义短语（custom_phrase.txt）的编码，如果前面出现顶功码时，会无法按照造词规则读取。  


改动说明：  
zh	f  
sh	j  
ch	k  
a	z  
e	d  
u	j    
i	k  
o	l  
uo	l  

*特别说明，需要恢复传统声笔，打开顶功规则，还需要替换会原来的词典  
  - sbjm            
  - sbxh_stroke  （主副方案都需要替换）  
  - sbxh_cz  
special: "^([a-z][aeuio][bpmfdtnlgkhjqxzhrzcsywv])"  


dict文件是两个大些的词典，使用方法，替换sbxh_cz.dict.yaml的内容，重新部署
