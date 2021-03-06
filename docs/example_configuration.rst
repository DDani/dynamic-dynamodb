.. _example_configuration_file:

Example configuration file
==========================

This is a full example of a Dynamic DynamoDB configuration file.
::

    [global]
    # AWS access keys
    aws-access-key-id: AWS_ACCESS_KEY
    aws-secret-access-key-id: AWS_SECRET_KEY

    # AWS region to use
    region: us-east-1

    # How often should Dynamic DynamoDB monitor changes (in seconds)
    check-interval: 300

    # Circuit breaker configuration
    # No provisioning updates will be made unless this URL returns
    # a HTTP 200 OK status code
    #circuit-breaker-url: http://my.service.com/v1/is_up
    #circuit-breaker-timeout: 500

    [logging]
    # Log level [debug|info|warning|error]
    log-level: info

    # Log file (comment out to get only console output)
    log-file: /var/log/dynamic-dynamodb.log


    [table: ^my_table$]
    #
    # Read provisioning configuration
    #

    # Thresholds for scaling up or down the provisioning (%)
    reads-upper-threshold: 90
    reads-lower-threshold: 30

    # How many percent should Dynamic DynamoDB increase/decrease provisioning with (%)
    increase-reads-with: 50
    decrease-reads-with: 50

    # Units to increase or decrease reads with, must be either percent or units
    increase-reads-unit: percent
    decrease-reads-unit: percent

    # Maximum and minimum read provisioning
    # Dynamic DynamoDB will not provision any more or less reads than this
    #min-provisioned-reads: 100
    #max-provisioned-reads: 500

    #
    # Write provisioning configuration
    #

    # Thresholds for scaling up or down the provisioning (%)
    writes-upper-threshold: 90
    writes-lower-threshold: 30

    # How many percent should Dynamic DynamoDB increase/decrease provisioning with (%)
    increase-writes-with: 50
    decrease-writes-with: 50

    # Units to increase or decrease writes with, must be either percent or units
    increase-writes-unit: percent
    decrease-writes-unit: percent

    # Maximum and minimum write provisioning
    # Dynamic DynamoDB will not provision any more or less writes than this
    #min-provisioned-writes: 100
    #max-provisioned-writes: 500

    #
    # Maintenance windows (in UTC)
    #
    #maintenance-windows: 22:00-23:59,00:00-06:00

    #
    # Other settings
    #

    # Allow down scaling when at 0% consumed reads
    #allow-scaling-down-reads-on-0-percent: true
    #allow-scaling-down-writes-on-0-percent: true

    # Restric scale down to only happen when BOTH reads AND writes are in need
    # of scaling down. Set this to "true" to minimize down scaling.
    #always-decrease-rw-together: true

    [gsi: ^my_gsi$ table: ^my_table$]
    #
    # Read provisioning configuration
    #

    # Thresholds for scaling up or down the provisioning (%)
    reads-upper-threshold: 90
    reads-lower-threshold: 30

    # How many percent should Dynamic DynamoDB increase/decrease provisioning with (%)
    increase-reads-with: 50
    decrease-reads-with: 50

    # Units to increase or decrease reads with, must be either percent or units
    increase-reads-unit: percent
    decrease-reads-unit: percent

    # Maximum and minimum read provisioning
    # Dynamic DynamoDB will not provision any more or less reads than this
    #min-provisioned-reads: 100
    #max-provisioned-reads: 500

    #
    # Write provisioning configuration
    #

    # Thresholds for scaling up or down the provisioning (%)
    writes-upper-threshold: 90
    writes-lower-threshold: 30

    # How many percent should Dynamic DynamoDB increase/decrease provisioning with (%)
    increase-writes-with: 50
    decrease-writes-with: 50

    # Units to increase or decrease writes with, must be either percent or units
    increase-writes-unit: percent
    decrease-writes-unit: percent

    # Maximum and minimum write provisioning
    # Dynamic DynamoDB will not provision any more or less writes than this
    #min-provisioned-writes: 100
    #max-provisioned-writes: 500

    #
    # Maintenance windows (in UTC)
    #
    #maintenance-windows: 22:00-23:59,00:00-06:00

    #
    # Other settings
    #

    # Allow down scaling when at 0% consumed reads
    #allow-scaling-down-reads-on-0-percent: true
    #allow-scaling-down-writes-on-0-percent: true

    # Restric scale down to only happen when BOTH reads AND writes are in need
    # of scaling down. Set this to "true" to minimize down scaling.
    #always-decrease-rw-together: true

Note: The configuration of tables support regular expressions so you could write ``[table: log_* ]`` if you want to target multiple tables with one config section.
