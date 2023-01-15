

# xml parser to grab secrets from xml file

  

~~~~

xmlint --xpath "jnlp/application-desc/arguement [1]/text()" file.jnlp > file.secrets

~~~~