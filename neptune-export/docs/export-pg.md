    NAME
            neptune-export.sh export-pg - Export property graph from Neptune to CSV
            or JSON
    
    SYNOPSIS
            neptune-export.sh export-pg [ {-cn | --concurrency} <concurrency> ]
                    {-d | --dir} <directory> {-e | --endpoint} <endpoints>...
                    [ {-el | --edge-label} <edgeLabels>... ] [ --format <format> ]
                    [ --log-level <logLevel> ]
                    [ {-nl | --node-label} <nodeLabels>... ]
                    [ {-p | --port} <port> ] [ {-r | --range} <range> ]
                    [ {-s | --scope} <scope> ] [ --sample ]
                    [ --sample-size <sampleSize> ] [ {-t | --tag} <tag> ]
                    [ --use-iam-auth ]
    
    OPTIONS
            -cn <concurrency>, --concurrency <concurrency>
                Concurrency (optional)
    
                This option may occur a maximum of 1 times
    
    
            -d <directory>, --dir <directory>
                Root directory for output
    
                This option may occur a maximum of 1 times
    
    
                This options value must be a path to a directory. The provided path
                must be readable and writable.
    
    
            -e <endpoints>, --endpoint <endpoints>
                Neptune endpoint(s) – supply multiple instance endpoints if you
                want to load balance requests across a cluster
    
            -el <edgeLabels>, --edge-label <edgeLabels>
                Labels of edges to be exported (optional, default all labels)
    
            --format <format>
                Output format (optional, default 'csv')
    
                This options value is restricted to the following set of values:
                    csv
                    json
    
                This option may occur a maximum of 1 times
    
    
            --log-level <logLevel>
                Log level (optional, default 'error')
    
                This options value is restricted to the following set of values:
                    trace
                    debug
                    info
                    warn
                    error
    
                This option may occur a maximum of 1 times
    
    
            -nl <nodeLabels>, --node-label <nodeLabels>
                Labels of nodes to be exported (optional, default all labels)
    
            -p <port>, --port <port>
                Neptune port (optional, default 8182)
    
                This option may occur a maximum of 1 times
    
    
                This options value represents a port and must fall in one of the
                following port ranges: 1024-49151
    
    
            -r <range>, --range <range>
                Range (optional)
    
                This option may occur a maximum of 1 times
    
    
            -s <scope>, --scope <scope>
                Scope (optional, default 'all')
    
                This options value is restricted to the following set of values:
                    all
                    nodes
                    edges
    
                This option may occur a maximum of 1 times
    
    
            --sample
                Select only a subset of nodes and edges when generating property
                metadata
    
                This option may occur a maximum of 1 times
    
    
            --sample-size <sampleSize>
                Property metadata sample size (optional, default 1000
    
                This option may occur a maximum of 1 times
    
    
            -t <tag>, --tag <tag>
                Directory prefix (optional)
    
                This option may occur a maximum of 1 times
    
    
            --use-iam-auth
                Use IAM database authentication to authenticate to Neptune
                (remember to set SERVICE_REGION environment variable)
    
                This option may occur a maximum of 1 times
    
    
    EXAMPLES
            bin/neptune-export.sh export-pg -e neptunedbcluster-xxxxxxxxxxxx.cluster-yyyyyyyyyyyy.us-east-1.neptune.amazonaws.com -d /home/ec2-user/output
    
                Export all data to the /home/ec2-user/output directory
    
            bin/neptune-export.sh export-pg -e neptunedbcluster-xxxxxxxxxxxx.cluster-yyyyyyyyyyyy.us-east-1.neptune.amazonaws.com -d /home/ec2-user/output --format json
    
                Export all data to the /home/ec2-user/output directory as JSON
    
            bin/neptune-export.sh export-pg -e neptunedbcluster-xxxxxxxxxxxx.cluster-yyyyyyyyyyyy.us-east-1.neptune.amazonaws.com -d /home/ec2-user/output -s nodes
    
                Export only nodes to the /home/ec2-user/output directory
    
            bin/neptune-export.sh export-pg -e neptunedbcluster-xxxxxxxxxxxx.cluster-yyyyyyyyyyyy.us-east-1.neptune.amazonaws.com -d /home/ec2-user/output -nl User -el FOLLOWS
    
                Export only User nodes and FOLLOWS relationships
    
            bin/neptune-export.sh export-pg -e neptunedbcluster-xxxxxxxxxxxx.cluster-yyyyyyyyyyyy.us-east-1.neptune.amazonaws.com -d /home/ec2-user/output -cn 2
    
                Parallel export using 2 threads
    
            bin/neptune-export.sh export-pg -e neptunedbcluster-xxxxxxxxxxxx.cluster-yyyyyyyyyyyy.us-east-1.neptune.amazonaws.com -d /home/ec2-user/output -cn 2 -r 1000
    
                Parallel export using 2 threads, with each thread processing
                batches of 1000 nodes or edges
    