
# return absolute path
function absPath {
  echo $(cd $(dirname "$1"); pwd)/$(basename "$1")
}


# Find location of this script

sdir="`cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd`"

solr_distrib="$sdir/../../.."

echo `absPath $solr_distrib`


