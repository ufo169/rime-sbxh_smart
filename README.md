*全顶功变动比较多，没必要，不建议折腾，建议使用dict文件夹里的传统声笔小鹤*   

主要更新英文输入，编码规律首字母大写，避免顶功的存在，导致英文不能连续输入：	  
  使用说明：	  
  ①手机端，利用shift按键特性，单击shift按键，首字母大写并临时转为英文输入。	   
    所以，单击shift按键后，就可以输入英文单词和中英混输部分，输入完上屏后，	   
    会自动转回中文输入。	   
    双击后shift按键，固定为大写字母输入，这时可以随意进行英文单词和连续句子	  
    输入，并且会自动分词带空格。也可以符号顶屏。输入完英文后，点击shift按键	 
    才可以回到中文输入。	   
  ②电脑端，需要（shift+首字母）可以临时转为首字母大写的输入方式，输入英文单词	  
    和中英混输部分，输入完上屏后，就会自动转回中文输入。	     
    *点击Caps_Lock后，固定为大写字母输入时，功能按键的缺失*	   
    所以需要完美的英文输入体验，推荐另外配置一个英文方案，再设置Ctrl按键快速	  
    切换方案，切换到英文方案后，可以连续输入，自动分词带空格，首字母大写，精准	  
    英文造词功能等  	  
    
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
*bn相当于第n个字的首笔*  

data：（自己可以查看输入编码或修改）  
日期：orq  
时间：osj  
星期：oxq  
季节：ojj  

` 引导拼音反查  
i 引导重复上屏  
；引导快符输入  
/ 引导表情符号（输入编码可以查看mysymbols.yaml）  
o 引导符号输入（输入编码可以查看o_symbols.dict.yaml）  
' 引导手动造词  
如：'mooe'lia'nn	魔力鸟，空格上屏后，词组便可以按照规则打  
*注意中间的分隔符‘可以不要（'mooeliann）  

*注意：手动造词，如果完整规则编码前面出现顶功时，会出现无法按照造词规则读取的情况。  
      自定义短语（custom_phrase.txt）的编码，需要首字母大写避免顶功规则。 

全顶功声笔，改动说明（详细查看README.md）：  
笔画键位声韵母变动：  
	zh 	  --→  	  f  
	sh 	  --→  	  j  
	ch 	  --→  	  k  
	a  	  --→  	  z  
	e  	  --→  	  d  
	u  	  --→  	  j  
	i  	  --→  	  k  
	o  	  --→  	  l  
	uo 	  --→  	  l  
字根：每个字的首笔是字根的，就用对应的字母代替这字根的笔顺（简单韵母音记忆，氵是 a）  
	日  	  	--→	  i  
	月  	  	--→	  e  
	人（亻）	--→	  e  
	口  	  	--→	  o  
	手（扌）	--→	  o  
	金（钅）	--→	  i  
	木  	  	--→	  u  
	水（氵）	--→	  a  
	土  	  	--→	  u  
	草（艹）	--→	  a  
	
*特别说明，需要恢复传统声笔，主方案sbxh_smart打开顶功规则，还需要替换以下三个原来未改动的词典  
  - sbjm  
  - sbxh_stroke  
  - sbxh_cz  
special: "^([a-z][aeuio][bpmfdtnlgkhjqxzhrzcsywv])"  
*简单的可以拿dict文件夹里的文件替换*  

dict文件是其它版本的词典，每个词典都是独立编码，自行选择。  
使用方法，替换sbxh_cz.dict.yaml的内容，重新部署  
