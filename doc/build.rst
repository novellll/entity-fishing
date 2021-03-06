.. topic:: Build and install NERD.

Install, build and run
======================

*entity-fishing* requires JDK 1.8 and maven 3. It supports Linux-64 and Mac OS environments. Below, we make available the LMDB binary data for these two architectures. 

Running the service requires at least 3GB of RAM, but more RAM will be exploited if available for speeding up access to the compiled Wikidata and Wikipedia data (including Wikidata statements associated to entities).
After decompressing all the index data, up to 80 GB of disk space will be used if you wish to use all the supported languages (en, fr, de , it, es) - be sure to have enough free space. For running English language only, you will need around 35GB. 
SSD is recommended for best performance and experience, in particular with a low amount of available RAM (e.g. RAM < 4GB).

First install ``GROBID`` and ``grobid-ner``, see the relative instruction of `GROBID <http://github.com/kermitt2/grobid>`_ and `grobid-ner <http://github.com/kermitt2/grobid-ner>`_.

The path to grobid-home shall indicated in the file ``data/config/mention.yaml``, for instance:
::
   # path to the GROBID home (for grobid-ner, grobid, etc.)
   grobidHome: ../grobid/grobid-home/

Install *entity-fishing*:
::
   $ git clone https://github.com/kermitt2/nerd


Then install the compiled indexed data:

#. Download the zipped data files corresponding to your environment and to your languages of choice (warning: total is around 23.3 GB, compressed) at the following links:

    **Linux**

        - https://science-miner.s3.amazonaws.com/entity-fishing/0.0.3/linux/db-kb.zip (4.1 GB)

        - https://science-miner.s3.amazonaws.com/entity-fishing/0.0.3/linux/db-en.zip (8.3 GB)

        - https://science-miner.s3.amazonaws.com/entity-fishing/0.0.3/linux/db-fr.zip (2.9 GB)

        - https://science-miner.s3.amazonaws.com/entity-fishing/0.0.3/linux/db-de.zip (3.8 GB)

        - https://science-miner.s3.amazonaws.com/entity-fishing/0.0.3/linux/db-es.zip (2.2 GB)

        - https://science-miner.s3.amazonaws.com/entity-fishing/0.0.3/linux/db-it.zip (2.0 GB)


    **MacOS**

        - https://science-miner.s3.amazonaws.com/entity-fishing/0.0.3/macos/db-kb.zip (4.1 GB)

        - https://science-miner.s3.amazonaws.com/entity-fishing/0.0.3/macos/db-en.zip (5.5 GB)

        - https://science-miner.s3.amazonaws.com/entity-fishing/0.0.3/macos/db-fr.zip (1.9 GB)

        - https://science-miner.s3.amazonaws.com/entity-fishing/0.0.3/macos/db-de.zip (2.0 GB)

        - https://science-miner.s3.amazonaws.com/entity-fishing/0.0.3/macos/db-es.zip (1.5 GB)

        - https://science-miner.s3.amazonaws.com/entity-fishing/0.0.3/macos/db-it.zip (1.3 GB)



#. Unzip the 6 first db archives files under ``data/db/``.

    This will install several sub-directories, one per language, plus wikidata (``db-kb``): ``data/db/db-XY/``, with XY equal to ``fr``, ``en``, ``it``, ``es``, ``en``
    The uncompressed data is about 80 GB.

#. Build the project, under the *entity-fishing* project repository.
   ::
      $ mvn clean install

   Some tests will be executed. If all tests are successful, you should be now ready to run the service.

 
#. Run the service:
   ::
      $ mvn clean jetty:run

The test console is available at port ``:8090`` by opening in your browser (preferably *Firefox* or *Chrome*, *Internet Explorer* has not been tested): http://localhost:8090

For more information, see the next section on the *entity-fishing* Console.
