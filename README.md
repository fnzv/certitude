CERTitude - The seeker of IOC
=============

# Main purpose

CERTitude is a Python-based tool which aims at assessing the compromised perimeter during incident response assignments.



# Install guide

## Submodules notice

CERTitude now relies on submodules.
- When initially cloning the repo, dont forget to do `git clone --recurse-submodules [url]`.
- If updating an already cloned repo, do `git submodule init` then `git submodule update`

## Software Requirements

- Python >= 2.7.9
- OpenSSL if you want to use SSL


## Installing Python requirements

### Virtualenv

CERTitude is compatible with virtualenv.
Install it with `pip install virtualenv`.
In the root directory, type:

```
virtualenv .
. ./bin/activate
```


### Commands

```batch
cd dist
cd plyara
python setup.py build
python setyp.py install
cd ..
pip install --upgrade pip
pip install lxml-3.6.0-cp27-none-win32.whl	# Under ...
.\pycrypto-2.6.1.win32-py2.7.exe			# ... Windows
pip install -r requirements.txt
```


## Generating SSL certificate & private key

**Note:** this steps requires openssl to be installed and in your `$PATH`

```batch
cd ssl
gen-cert-for-me.bat
```


## Tweaking your config file

Edit `config.py`

- Enable HTTPS:
    - `USE_SSL=True`
    - `SSL_KEY_FILE = 'path/to/key'`
    - `SSL_CERT_FILE = 'path/to/cer'`

- Database location: `BASE_DE_DONNEES_QUEUE = 'path/to/db'`
- Set the server SALT for password hashing (based on sha256)


# Run guide

## Initializing the database

`python main.py init`


## Runnning things

- Interface : `python main.py run -c interface`
- Scanner : `python main.py run -c iocscan [-b batch]`


# Misc

## Contact

cert@wavestone.com
&copy; Wavestone 2016


## Available modules

```
*** IOCSCAN ***
ProcessItem     pid, parentpid, UserSID, Username, name, path, moduleList
MemoryItem      pid, parentpid, name, page_addr, page_size, access_read, access_write, access_execute, access_copy_on_write
RegistryItem    KeyPath, ValueName
ArpEntryItem    Interface, IPv4Address, PhysicalAddress, CacheType
PrefetchItem    PrefetchHash, ApplicationFileName, ReportedSizeInBytes, SizeInBytes, TimesExecuted, FullPath
ServiceItem     descriptiveName, mode, path, pathmd5sum, status, name
DnsEntryItem    RecordName, RecordType, TimeToLive, DataLength, RecordData/Host, RecordData/IPv4Address
PortItem        protocol, localIP, localPort, remoteIP, remotePort, state, pid
FileItem        FilePath, FullPath, FileExtension, FileName


*** HashSCAN ***
FileItem        FilePath, Md5Sum, Sha1Sum, Sha256Sum
```

## Contributors

### Developers 

- Aurélien BAUD
- Adrien DEGRANGE
- Thomas LABADIE
- Jean MARSAULT
- Vincent NGUYEN
- Fabien SCHWEBEL
- Antoine VALLEE


### External dependencies

- Plyara : https://github.com/8u1a/plyara/